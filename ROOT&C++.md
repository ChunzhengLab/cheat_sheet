 

````C++
//C++按时间抽取随机数，shuffle vector
#include <algorithm>    // std::shuffle
#include <random>       // std::default_random_engine
#include <chrono>       // std::chrono::system_clock
double<vector> myvector;
unsigned seed = std::chrono::system_clock::now().time_since_epoch().count();
shuffle(myvector.begin(),myvector.end(),std::default_random_engine(seed));
````

```C++
//遍历文件与文件夹，利用POSIX的dirent功能
#include <stdio.h>
#include <dirent.h>
int main(int argc, const char**argv) {
    struct dirent *entry = nullptr;
    DIR *dp = nullptr;

    dp = opendir(argc > 1 ? argv[1] : "/");
    if (dp != nullptr) {
        while ((entry = readdir(dp)))
            printf ("%s\n", entry->d_name);
    }

    closedir(dp);
    return 0;
}

//C++17标准库
#include <filesystem>
namespace fs = std::filesystem;
const fs::path pathToShow{ argc >= 2 ? argv[1] : fs::current_path() };
for (const auto& entry : fs::directory_iterator(pathToShow)) {
    const auto filenameStr = entry.path().filename().string();
    //支持判断是文件还是文件夹
    if (entry.is_directory())         std::cout << "dir:  " << filenameStr << '\n';
    else if (entry.is_regular_file()) std::cout << "file: " << filenameStr << '\n';
    else                              std::cout << "??    " << filenameStr << '\n';
  }
```



```C++
//得到当前文件所在路径
#include <unistd.h>
#include <sys/stat.h>

char pathbuf[100];
getcwd(pathbuf,sizeof(pathbuf));//获得当前目录下的绝对路径
```



```C++
//TList
TList* list = new TList();
list->Add(hist_1);//将hist_1加入list
list->Add(hist_2);//将hist_2加入list
TFile* outputFile = newTFile("output.root","RECREATE");
list->Write();//将加入list的object全部写入output.root
```



```C++
//TDirectory 为输出的.root文件创建文件夹
//写
TFile* outputFile = new TFile("output.root","RECREATE");
TDirectory *folder_1 = outputFile->mkdir("Folder_1");
TDirectory *folder_2 = outputFile->mkdir("Folder_2");

folder_1->cd();
hist_1->Write();
folder_2->cd();
hist_2->Write();

//读
TFile* inputFile = new TFile("output.root","READ");
TDirectory* inputDir_1 = inputFile->GetDirectory("folder_1");
TDirectory* inputDir_2 = inputFile->GetDirectory("folder_2");

TH1D* histRead_1 = NULL;
inputDir_1->GetObject("hist_1", histRead_1);
TH1D* histRead_2 = NULL;
inputDir_2->GetObject("hist_2", histRead_2);

histRead_1->Draw();
```
