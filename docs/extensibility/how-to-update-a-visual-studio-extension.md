---
title: 'Porady: aktualizowanie rozszerzenie programu Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c37f26ed8215bb7eac360c978ba902c8e95975ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-update-a-visual-studio-extension"></a>Porady: aktualizowanie rozszerzenie programu Visual Studio
Można zaktualizować rozszerzenia programu Visual Studio na komputerze przy użyciu **rozszerzenia i aktualizacje** Aby zainstalować zaktualizowaną wersję. Jeśli tworzysz zaktualizowaną wersję rozszerzenia, oznaczyć go jako zaktualizowany przez zwiększenie numeru wersji w manifeście VSIX.  
  
 Aktualizacje są instalowane przy manifestu VSIX przychodzące rozszerzenia ma taką samą `ID` jako jeden zainstalowany i wyższe `Version` numer. Jeśli `Version` numer jest taki sam lub niższy, nie można zainstalować pakietu. Jeśli `ID` wartości nie są zgodne, pakietu, który nie został jeszcze zainstalowany jest rozpoznawana jako osobne rozszerzenia.  
  
 Aby uniknąć konfliktów podczas tworzenia, zaleca się, czy odinstalować starszych wersji rozszerzenia w toku, a także Odinstaluj lub wyłącz inne rozszerzenia mogą powodować konflikt.  
  
### <a name="to-update-an-extension-on-your-system"></a>Aby zaktualizować rozszerzenia w systemie  
  
1.  Na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.  
  
2.  W okienku po lewej stronie kliknij **aktualizacje**.  
  
3.  W środkowym okienku kliknij aktualizację, którą chcesz zainstalować.  
  
     Numer wersji rozszerzenia zaktualizowane jest wyświetlana w okienku po prawej stronie, oraz inne informacje.  
  
4.  W dolnej części okienku po prawej stronie, kliknij przycisk **aktualizacji**.  
  
### <a name="to-publish-an-update-of-an-extension"></a>Aby opublikować aktualizację rozszerzenia  
  
1.  W programie Visual Studio Otwórz rozwiązanie rozszerzenie, które chcesz zaktualizować. Wprowadź zmiany.  
  
    > [!IMPORTANT]
    >  Niepodpisane wszystkie rozszerzenia użytkownika zostanie zaktualizowana automatycznie. Należy zawsze utworzyć rozszerzeń.  
  
2.  W **Eksploratora rozwiązań**, otwórz source.extension.manifest.  
  
3.  W Projektancie manifestu, zwiększ wartość numeru w **wersji** pola.  
  
4.  Zapisz rozwiązanie i jego tworzenia.  
  
5.  Przekaż nowy plik .vsix (w folderze \bin\Debug\ projektu) do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) witryny sieci Web.  
  
     Po otwarciu użytkownik, który ma wcześniejszej wersji rozszerzenia **rozszerzenia i aktualizacje**, nowa wersja pojawi się w **aktualizacje** listy, pod warunkiem, że narzędzie ma ustawioną wartość automatycznie wyszukać aktualizacje.  
  
     Można włączyć lub wyłączyć automatyczne sprawdzanie aktualizacji w dolnej części **aktualizacje** okienka (**Włącz/Wyłącz automatyczne wykrywanie dostępnych aktualizacji**), które zmiany **Wyszukaj aktualizacje** w **narzędzia / Opcje / środowiska / rozszerzenia i aktualizacje**.  
  
    > [!NOTE]
    >  Począwszy od programu Visual Studio 2015 Update 2, można określić (w **narzędzia / Opcje / środowiska / rozszerzenia i aktualizacje**) czy będzie aktualizacji automatycznych dla rozszerzeń dla poszczególnych użytkowników, wszystkie rozszerzenia użytkownika lub obu (ustawienie domyślne).  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich](../ide/finding-and-using-visual-studio-extensions.md)
