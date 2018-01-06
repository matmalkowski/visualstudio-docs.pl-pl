---
title: "Jak używać Google testu dla języka C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4868fae-fd6d-4b98-a85f-f23b0dd2fca5
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7655c8690c48657c9efab967851ceff43c253135
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Jak używać Google testu dla języka C++ w programie Visual Studio
W **programu Visual Studio 2017 wersji 15,5 cala** i później, Google testu jest zintegrowany z programu Visual Studio IDE jako część domyślnego **Develoment pulpitu z C++** obciążenia. Aby sprawdzić, czy jest zainstalowany na tym komputerze, otwórz Instalator programu Visual Studio i Znajdź Google Test na liście składników obciążenia:

![Zainstaluj usługi Google testu](media/cpp-google-component.png "zainstalować Google testu dla języka C++")

## <a name="add-a-google-test-project-to-the-solution"></a>Dodaj projekt testowy Google do rozwiązania
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz **Dodaj | Nowy projekt**. 
2. W okienku po lewej stronie wybierz **Visual C++ | Test** , a następnie wybierz **projekt testowy Google** w środkowym okienku. 
3. Nadaj nazwę projektu testowego, a następnie kliknij przycisk **OK**. 

![Nowy projekt testowy Google](media/cpp-gtest-new-project.png "dodać nowy projekt testowy Google")

## <a name="configure-the-test-project"></a>Konfigurowanie projektu testowego
W **przetestować konfigurację projektu** okna dialogowego wyświetlanego, możesz wybrać projekt ma zostać przetestowana. Po wybraniu projektu programu Visual Studio dodaje odwołanie do wybranego projektu. Jeśli żaden projekt, musisz ręcznie dodać odwołań do projektów, które mają zostać przetestowane. W przypadku wybrania między statycznych i dynamicznych łączenia plików binarnych testów Google, zagadnienia są takie same jak dla dowolnego programu C++. Aby uzyskać więcej informacji, zobacz [biblioteki dll w programie Visual C++](/cpp/build/dlls-in-visual-cpp). 

 ![Konfigurowanie projektu testowego Google](media/cpp-gtest-config.png "skonfigurować projekt testowy Google")

## <a name="set-additional-options"></a>Ustaw dodatkowe opcje.
W menu głównym wybierz **narzędzia | Opcje | Adapter testu dla testu Google** można ustawić dodatkowe opcje. Zobacz dokumentację programu Google testu Aby uzyskać więcej informacji o tych ustawieniach.

 ![Ustawienia projektu testowego Google](media/cpp-gtest-settings.png "ustawienia projektu testowego Google")

## <a name="add-include-directives"></a>Dodaj dyrektyw
W pliku .cpp testowego, Dodaj wszelkie potrzebne `#include` dyrektywy, aby wyświetlić typy i funkcje programu kod testu. Zazwyczaj program działa jeden poziom w hierarchii folderów. W przypadku wpisania `#include "../"` są wyświetlane i umożliwia wybór pełną ścieżkę do pliku nagłówka okna IntelliSense.

![Dodaj # dyrektywy include](media/cpp-gtest-includes.png "Dodaj zawiera dyrektywy, które do pliku .cpp testu")

## <a name="write-and-run-tests"></a>Zapis i uruchamiania testów
Teraz można przystąpić do zapisu i uruchamiać testy Google. Zobacz [Elementarz Test Google](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md) informacji o makra testu. Zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md) informacji o odnajdywaniu, uruchamiania i grupowanie testów przy użyciu **Eksploratora testów**.

## <a name="see-also"></a>Zobacz też
[Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)


  







