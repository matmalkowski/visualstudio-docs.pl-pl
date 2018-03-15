---
title: Dokumentacja interfejsu API z Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload:
- multiple
author: mikeblome
ms.openlocfilehash: 3761b49e0c75b8b4b6676e6525f77c40c88ccf33
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Reference

W tym temacie wymieniono publiczne elementy członkowskie `Microsoft::VisualStudio::CppUnitTestFramework` przestrzeni nazw. Te interfejsy API umożliwia pisać testy jednostkowe C++ oparte na platformy testów jednostkowych natywnego firmy Microsoft. Brak [przykład użycia](#example) na końcu tego tematu.

 Pliki nagłówkowe znajdują się w *InstallFolder VisualStudio2012 [x 86] *** \VC\UnitTest\include** folderu.

 Pliki lib znajdują się w *InstallFolder VisualStudio2012 [x 86] *** \VC\UnitTest\lib** folderu.

Nagłówek i lib ścieżek zostaną automatycznie skonfigurowane w macierzystym projektu testowego.

##  <a name="In_this_topic"></a> W tym temacie
 [CppUnitTest.h](#cppUnitTest_h)

-   [Tworzenie testu klasy i metody](#create_test_classes_and_methods)

-   [Inicjowanie i oczyszczanie](#Initialize_and_cleanup)

    -   [Metody testowe](#test_methods)

    -   [Klasy testowe](#test_classes)

    -   [Moduły testu](#test_modules)

-   [Utwórz atrybuty testu](#create_test_attributes)

    -   [Atrybuty metody testu](#test_method_attributes)

    -   [Atrybuty klasy testu](#test_class_attributes)

    -   [Atrybuty modułów testu](#test_module_attributes)

    -   [Wstępnie zdefiniowanych atrybutów](#pre_defined_attributes)

     [CppUnitTestAssert.h](#cppUnitTestAssert_h)

    -   [Potwierdza, ogólne](#general_asserts)

        -   [Są takie same](#general_are_equal)

        -   [Nie są takie same](#general_are_not_equal)

        -   [Są takie Same](#general_are_same)

        -   [Nie są takie Same](#general_are_not_same)

        -   [Ma wartość Null](#general_is_null)

        -   [Nie ma wartości Null](#general_is_not_null)

        -   [Ma wartość True](#general_is_True)

        -   [Ma wartość False](#general_is_false)

        -   [Niepowodzenie](#general_Fail)

    -   [Potwierdza środowiska wykonawczego systemu Windows](#winrt_asserts)

        -   [Są takie same](#winrt_are_equal)

        -   [Są takie Same](#winrt_are_same)

        -   [Nie są takie same](#winrt_are_not_equal)

        -   [Nie są takie Same](#winrt_are_not_same)

        -   [Ma wartość Null](#winrt_is_null)

        -   [Nie ma wartości Null](#winrt_is_not_null)

    -   [Wyjątek potwierdzeń](#exception_asserts)

        -   [Oczekiwany wyjątek](#expect_exception)

         [CppUnitTestLogger.h](#cppunittestlogger_h)

        -   [Logger](#logger)

        -   [Napisz wiadomość](#write_message)
    -    [Przykład użycia](#example)

##  <a name="cppUnitTest_h"></a> CppUnitTest.h

###  <a name="create_test_classes_and_methods"></a> Tworzenie testu klasy i metody

```cpp
TEST_CLASS(className)
```

 Wymagany w przypadku każdej klasy zawierające metody testowe. Identyfikuje *className* jako klasy testowej. `TEST_CLASS` musi zostać zadeklarowany w zakresie namescape.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}

```

 Definiuje *methodName* jako metody testowej. `TEST_METHOD` musi być zadeklarowana w zakresie metody klasy.

###  <a name="Initialize_and_cleanup"></a> Inicjowanie i oczyszczanie

####  <a name="test_methods"></a> Metody testowe

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 Definiuje *methodName* jako metodę, która jest uruchamiana przed uruchomieniem każdej metody. `TEST_METHOD_INITIALIZE` można zdefiniować tylko raz w klasie testu i musi być zdefiniowana w klasie testu.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 Definiuje *methodName* jako metodę, która jest uruchamiana po uruchomieniu każdej metody. `TEST_METHOD_CLEANUP` można zdefiniować tylko raz w klasie testu i musi być zdefiniowana w zakresie klasy testowej.

####  <a name="test_classes"></a> Klasy testowe

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

 Definiuje *methodName* jako metodę, która jest uruchamiana po utworzeniu każdej klasy testowej. `TEST_CLASS_INITIALIZE` można zdefiniować tylko raz w klasie testu i musi być zdefiniowana w zakresie klasy testowej.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

 Definiuje *methodName* jako metodę, która jest uruchamiana po utworzeniu każdej klasy testowej. `TEST_CLASS_CLEANUP` można zdefiniować tylko raz w klasie testu i musi być zdefiniowana w zakresie klasy testowej.

####  <a name="test_modules"></a> Moduły testu

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Definiuje metodę *methodName* uruchamiany po załadowaniu modułu. `TEST_MODULE_INITIALIZE` można zdefiniować tylko raz w module testu i musi być zadeklarowana w zakresie przestrzeni nazw.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Definiuje metodę *methodName* systemem, gdy moduł jest zwolniony. `TEST_MODULE_CLEANUP` można zdefiniować tylko raz w module testu i musi być zadeklarowana w zakresie przestrzeni nazw.

###  <a name="create_test_attributes"></a> Utwórz atrybuty testu

####  <a name="test_method_attributes"></a> Atrybuty metody testu

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane z co najmniej jeden `TEST_METHOD_ATTRIBUTE` makra do metody testowej *testClassName*.

 A `TEST_METHOD_ATTRIBUTE` makro definiuje atrybut o nazwie *attributeName* i wartość *attributeValue*.

####  <a name="test_class_attributes"></a> Atrybuty klasy testu

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane z co najmniej jeden `TEST_CLASS_ATTRIBUTE` makra do klasy testowej *testClassName*.

 A `TEST_CLASS_ATTRIBUTE` makro definiuje atrybut o nazwie *attributeName* i wartość *attributeValue*.

####  <a name="test_module_attributes"></a> Atrybuty modułów testu

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane z co najmniej jeden `TEST_MODULE_ATTRIBUTE` makra do modułu test *testModuleName*.

 A `TEST_MODULE_ATTRIBUTE` makro definiuje atrybut o nazwie *attributeName* i wartość *attributeValue*.

####  <a name="pre_defined_attributes"></a> Wstępnie zdefiniowanych atrybutów
 Można zastąpić makr wstępnie zdefiniowanego atrybutu dla makra `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE`, lub `TEST_MODULE_ATTRIBUTE` opisane powyżej.

```cpp
TEST_OWNER(ownerAlias)
```

 Definiuje atrybut o nazwie `Owner` i wartość atrybutu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Definiuje atrybut o nazwie `Description` i wartość atrybutu *opis*.

```cpp
TEST_PRIORITY(priority)
```

 Definiuje atrybut o nazwie `Priority` i wartość atrybutu *priorytet*.

```cpp
TEST_WORKITEM(workitem)
```

 Definiuje atrybut o nazwie `WorkItem` i wartość atrybutu *workItem*.

```cpp
TEST_IGNORE()
```

 Definiuje atrybut o nazwie `Ignore` i wartość atrybutu `true`.

##  <a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

###  <a name="general_asserts"></a> Potwierdza, ogólne

####  <a name="general_are_equal"></a> Są takie same
 Sprawdź, czy dwa obiekty są takie same

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa symulacyjnych są takie same

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa elementów przestawnych są takie same

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa char * ciągi są takie same

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa ciągi w_char * są takie same

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_not_equal"></a> Nie są takie same
 Sprawdź dwóch symulacyjnych nie są takie same

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa elementów przestawnych nie są takie same

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa char * ciągów nie są takie same

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa ciągi w_char * nie są takie same

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa odwołania nie są takie same na podstawie operatora ==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_same"></a> Są takie Same
 Upewnij się, że dwa odwołania odwołują się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_not_same"></a> Nie są takie Same
 Upewnij się, że dwa odwołania nie odwołują się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_null"></a> Ma wartość Null
 Sprawdź, czy wskaźnik ma wartość NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_not_null"></a> Nie ma wartości Null
 Sprawdź, czy wskaźnik nie jest pusty

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_True"></a> Ma wartość True
 Sprawdź, czy warunek jest spełniony

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_false"></a> Ma wartość False
 Sprawdź, czy warunek jest FAŁSZ

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_Fail"></a> Niepowodzenie
 Wymuś pozwalającym wyniku przypadku testowego

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

###  <a name="winrt_asserts"></a> Potwierdza środowiska wykonawczego systemu Windows

####  <a name="winrt_are_equal"></a> Są takie same
 Sprawdza, czy dwa wskaźniki środowiska wykonawczego systemu Windows są takie same.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Weryfikuje, że dwa Platform::String ^ ciągi są takie same.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_same"></a> Są takie Same
 Sprawdza, czy dwa odwołania środowiska wykonawczego systemu Windows odwołują tego samego obiektu.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_not_equal"></a> Nie są takie same
 Sprawdza, czy dwóch wskaźników środowiska wykonawczego systemu Windows nie są takie same.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Weryfikuje, że dwa Platform::String ^ ciągów nie są takie same.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_not_same"></a> Nie są takie Same
 Sprawdza, czy dwa odwołania środowiska wykonawczego systemu Windows nie odwołuj się do tego samego obiektu.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_is_null"></a> Ma wartość Null
 Sprawdza, czy wskaźnik środowiska wykonawczego systemu Windows jest nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_is_not_null"></a> Nie ma wartości Null
 Sprawdza, czy wskaźnik środowiska wykonawczego systemu Windows nie jest nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

###  <a name="exception_asserts"></a> Wyjątek potwierdzeń

####  <a name="expect_exception"></a> Oczekiwany wyjątek
 Sprawdź, czy funkcja zgłasza wyjątek:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Sprawdź, czy funkcja zgłasza wyjątek:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

##  <a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

###  <a name="logger"></a> Rejestratora
 Klasa rejestratora zawiera metody statyczne do zapisu **okno danych wyjściowych**.

###  <a name="write_message"></a> Napisz wiadomość
Ciąg, aby zapisać **okno danych wyjściowych**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a> Przykład
 Ten kod jest przykładem użycia VSCppUnit. Zawiera przykłady atrybutu metadanych, osprzętu, testy jednostkowe z potwierdzeń i rejestrowania niestandardowego.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostek kodu](../test/unit-test-your-code.md)
- [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)

