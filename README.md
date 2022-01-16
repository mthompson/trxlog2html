# trxlog2html

Trxlog2html is the command line tool for converting the output result of VSTest log to html.



## converting sample

**The result of VSTest**

![test_explorer](https://user-images.githubusercontent.com/2186957/149645616-53d97b4e-c49d-4c95-b1dd-1812b916efff.PNG)



**The report html**

![test_html](https://user-images.githubusercontent.com/2186957/149645647-425f78b5-b4f0-482f-9517-dee63b3a73ef.PNG)



# How to use



## Output Visual Studio Test Result File (TRX)

(under construction)

Execute VSTest.Console.exe to output TRX log.

VSTest.Console.exe exists under the Visual Studio installation directory. Since it exists in a deep directory, it is recommended to create a batch like the one below.



```
@echo off
setlocal

REM edit VSTEST_DIR to suit youe environment.
SET VSTEST_DIR=C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE\CommonExtensions\Microsoft\TestWindow\

REM edit TEST_DLL_PATH to your test project dll path.
SET TEST_DLL_PATH=.\bin\Debug\.netcoreapp,version=v5.0\UnitTestSampleTests.dll

"%VSTEST_DIR%vstest.console.exe" %TEST_DLL_PATH% /logger:trx;LogFileName=utest_result.xml

endlocal
```



## Convert trx file to html

Execute the following command from the command prompt.

```
dotnet run trxlog2html -i [input trx file path] -o [output html file path]
```



# Customize output html format

(under construction)









