### C++ 20 `requires`关键字的一个用例

```c++
#include <iostream>

// 模拟 histos.fill 方法
struct Histos {
    void fill(const char* name, auto value) {
        std::cout << "Filling histogram " << name << " with value " << value << std::endl;
    }
} histos;

bool isCentralityRequired = true;

template <typename T>
void fillGeneralHistos(T& coll)
{
    // 检查 coll 是否具有 centFT0C 方法
    if constexpr (requires { coll.centFT0C(); }) {
        if (isCentralityRequired) {
            histos.fill("MC/control/centrality", coll.centFT0C());
        }
    }
}

// 示例类，有和没有 centFT0C 方法
struct ExampleWithCentrality {
    int centFT0C() const { return 50; }
};

struct ExampleWithoutCentrality {
    // 没有 centFT0C 方法
};

int main() {
    ExampleWithCentrality collWithCentrality;
    fillGeneralHistos(collWithCentrality); // OK，有 centFT0C 方法的类型

    ExampleWithoutCentrality collWithoutCentrality;
    fillGeneralHistos(collWithoutCentrality); // OK，没有 centFT0C 方法的类型

    return 0;
}
```

利用`requires`（结合 `constexpr`）,预先探知类`coll`是否包含`centFT0C()`方法。也可以依托传统的 SFINAE（Substitution Failure Is Not An Error）技巧实现以避免使用`constexpr`


