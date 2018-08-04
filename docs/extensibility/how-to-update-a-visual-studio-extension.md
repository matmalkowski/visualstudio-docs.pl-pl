---
title: 'Porady: aktualizowanie rozszerzenia programu Visual Studio | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 8bf951215dfb4f6837c157a7b8510fba2d09f140
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500190"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Porady: aktualizowanie rozszerzenia programu Visual Studio
Można zaktualizować rozszerzenia programu Visual Studio w systemie przy użyciu **rozszerzenia i aktualizacje** zainstalować zaktualizowaną wersję. Jeśli tworzysz zaktualizowaną wersję rozszerzenia, oznaczyć go jako zaktualizowany przez zwiększenie numeru wersji manifestu VSIX.  
  
 Aktualizacje są instalowane podczas manifestu VSIX przychodzących rozszerzenia ma taką samą `ID` jako zainstalowaną wersją i uzyskanie lepszej `Version` numer. Jeśli `Version` numer jest taki sam lub niższy, nie można zainstalować pakietu. Jeśli `ID` wartości nie są zgodne, pakiet, który nie jest jeszcze zainstalowany jest rozpoznawana jako osobne rozszerzenie.  
  
 Aby uniknąć konfliktów podczas programowania, zaleca się, czy odinstalowaniu wcześniejszych wersji rozszerzenia w toku, a także Odinstaluj lub wyłącz inne rozszerzenia mogą powodować konflikt.  
  
## <a name="to-update-an-extension-on-your-system"></a>Można zaktualizować rozszerzenia w systemie  
  
1.  Na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.  
  
2.  W okienku po lewej stronie kliknij **aktualizacje**.  
  
3.  W środkowym okienku kliknij aktualizacji, którą chcesz zainstalować.  
  
     Numer wersji zaktualizowane rozszerzenie jest wyświetlana w okienku po prawej stronie, oraz inne informacje.  
  
4.  W dolnym okienku po prawej stronie, kliknij **aktualizacji**.  
  
## <a name="to-publish-an-update-of-an-extension"></a>Aby opublikować aktualizację rozszerzenia  
  
1.  W programie Visual Studio Otwórz rozwiązanie dla rozszerzenia, które chcesz zaktualizować. Wprowadź zmiany.  
  
    > [!IMPORTANT]
    >  Niepodpisane wszystkie rozszerzenia użytkowników nie zostaje zaktualizowana automatycznie. Należy zawsze utworzyć rozszerzeń.  
  
2.  W **Eksploratora rozwiązań**, otwórz *source.extension.manifest*.  
  
3.  W Projektancie manifestu, należy zwiększyć wartość liczby w parametrze **wersji** pola.  
  
4.  Zapisywanie rozwiązania i skompiluj je.  
  
5.  Przekaż nowy *.vsix* pliku (w * \bin\Debug\* folder projektu) do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) witryny sieci Web.  
  
     Po otwarciu użytkownik, który ma wcześniejszą wersję rozszerzenia **rozszerzenia i aktualizacje**, nowa wersja pojawi się w **aktualizacje** listy, pod warunkiem, że narzędzie ma wartość automatycznie wyszukać aktualizacje.  
  
     Można włączyć lub wyłączyć automatyczne sprawdzanie dostępności aktualizacji w dolnej części **aktualizacje** okienko (**Włącz/Wyłącz automatyczne wykrywanie dostępnych aktualizacji**), które zmiany **Wyszukaj aktualizacje** w **narzędzia** > **opcje** > **środowiska**  >  **Rozszerzenia i aktualizacje**.  
  
    > [!NOTE]
    >  Począwszy od programu Visual Studio 2015 Update 2, można określić (w **narzędzia** > **opcje** > **środowiska**  >  **Rozszerzenia i aktualizacje**) czy będzie automatyczne aktualizacje dla rozszerzenia dla poszczególnych użytkowników, wszystkie rozszerzenia użytkowników lub obie (ustawienie domyślne).  
  
## <a name="see-also"></a>Zobacz także  
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Wyszukiwanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)