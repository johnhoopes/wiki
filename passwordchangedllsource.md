<!-- TITLE: Passwordchangedllsource -->
<!-- SUBTITLE: A quick summary of Passwordchangedllsource -->

# Header

```c_cpp
#include <windows.h>
#include <stdio.h>


//How to build
//d:
//cd \MinGW\bin
//D:\MinGW\bin>gcc -c -DBUILD_DLL c:\Users\Tilver\source\repos\OpenPasswordFilter\HoopesMingwVersion\dllmain.cpp
//D:\MinGW\bin>gcc -shared -o test.dll dllmain.o


bool __stdcall APIENTRY DllMain(HMODULE hModule, DWORD  ul_reason_for_call, LPVOID lpReserved) {

        WSADATA wsa;

        switch (ul_reason_for_call) {
        case DLL_PROCESS_ATTACH:
        case DLL_THREAD_ATTACH:
        case DLL_THREAD_DETACH:
        case DLL_PROCESS_DETACH:
                break;
        }
        return true;
}

extern "C" __declspec(dllexport) bool __stdcall InitializeChangeNotify(void) {
        return true;
}

extern "C" __declspec(dllexport) int __stdcall PasswordChangeNotify(char *UserName,
  unsigned long RelativeId,
  char *NewPassword) {
        //Note that these are unicode strings
        return 0;
}

extern "C" __declspec(dllexport) BOOLEAN __stdcall PasswordFilter(char *AccountName,
  char *FullName,
  char *Password,
  bool SetOperation) {

        //Eventually I will use this.
        FILE *f = NULL;

        //Password is fine for now
        return true;
}

```
