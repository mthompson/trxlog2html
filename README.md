# trxlog2html

Trxlog2html is the command line tool for converting the output result of VSTest log to html.



## converting sample

**The result of VSTest**

![test_explorer](https://user-images.githubusercontent.com/2186957/149645616-53d97b4e-c49d-4c95-b1dd-1812b916efff.PNG)



**The report html**

![test_html](https://user-images.githubusercontent.com/2186957/149645647-425f78b5-b4f0-482f-9517-dee63b3a73ef.PNG)



# Install

You can install this tool from NuGet.org.



**.NET CLI(Global)**

Install as global tool.

```
dotnet tool install --global trxlog2html --version 1.0.0
```



**.NET CLI(Local)**

Install as local tool

```
dotnet new tool-manifest
dotnet tool install --local trxlog2html --version 1.0.0
```



*) Difference between global tool and local tool

https://docs.microsoft.com/en-us/dotnet/core/tools/global-tools



# How to use

Use the following procedure.

1. Run visual studio test and output a Visual Studio Test Results File (TRX).
2. Convert the TRX to html file using the trxlog2html tool.



The details are explained below.



## Run visual studio test and output TRX

To output TRX, you need to run Visual Studio tests from the command line using VSTest.Console.exe.

VSTest.Console.exe exists under the Visual Studio installation directory. Since it exists in a deep directory, it is recommended to create a batch like the one below.



```
@echo off
setlocal

REM edit VSTEST_DIR to suit your environment.
SET VSTEST_DIR=C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE\CommonExtensions\Microsoft\TestWindow\

REM edit TEST_DLL_PATH to your test project dll path.
SET TEST_DLL_PATH=.\bin\Debug\.netcoreapp,version=v5.0\UnitTestSampleTests.dll

"%VSTEST_DIR%vstest.console.exe" %TEST_DLL_PATH% /logger:trx;LogFileName=utest_result.xml

endlocal
```



*)See below for more information on VSTest.Console.exe.

https://github.com/MicrosoftDocs/visualstudio-docs/blob/main/docs/test/vstest-console-options.md



## Convert the TRX to html file

Execute the following command from the command prompt.

```
dotnet run trxlog2html -i [input trx file path] -o [output html file path]
```



# Customize output html format

You can use your own template to output an html file with the -t option.

```
dotnet run trxlog2html -i [input trx file path] -t [your_template_file] -o [output html file path]
```



The template is a Razor template format file (cshtml).

By default, the following built-in template is used. Please customize and use it.

https://github.com/HikosakaRyo/trxlog2html/blob/main/built_in_templates/jstest_like.cshtml







