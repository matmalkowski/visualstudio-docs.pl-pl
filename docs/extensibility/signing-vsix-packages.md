---
title: Podpisywanie pakietów VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1179f1fa6b642f7f2523699332ec64ccc13e4b8f
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36233558"
---
# <a name="signing-vsix-packages"></a>Podpisywanie pakietów VSIX
Zestawy rozszerzenia nie muszą być podpisane, zanim zostaną one uruchomione w programie Visual Studio, ale jest dobrym rozwiązaniem, aby to zrobić.  
  
 Jeśli chcesz zabezpieczyć rozszerzenie i upewnij się, że nie została zmieniona z dodaniem podpis cyfrowy do pakietu VSIX. Po podpisaniu VSIX Instalatora VSIX zostanie wyświetlony komunikat wskazujący, że on jest podpisany, oraz więcej informacji na temat samym podpisie. Jeśli zmodyfikowano zawartość pliku VSIX pliku VSIX nie została ponownie podpisana, Instalator VSIX wykaże, czy podpis jest nieprawidłowy. Instalacja nie zostanie zatrzymana, ale użytkownik jest ostrzeżenie.  
  
> [!IMPORTANT]
>  Począwszy od 2015 pakietów VSIX podpisany przy użyciu innym niż SHA256 szyfrowania zostaną zidentyfikowane jako posiadające nieprawidłowy podpis. VSIX instalacji nie zostanie zablokowany, ale użytkownik zostanie wyświetlone ostrzeżenie.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Podpisywanie pliku VSIX z VSIXSignTool  
 Jest dostępna z narzędzia podpisywania szyfrowania SHA256 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) na nuget.org w [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Aby użyć VSIXSignTool  
  
1.  Dodaj z pliku VSIX do projektu.  
  
2.  Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań, wybierając **Dodaj &#124; Zarządzaj pakietami NuGet**.  Aby uzyskać więcej informacji na NuGet i dodawanie NuGet Zobacz pakiety [dokumentacji NuGet](/NuGet) i [interfejsu użytkownika Menedżera pakietów](/NuGet/Tools/Package-Manager-UI) tematów.  
  
3.  Wyszukaj VSIXSignTool z VisualStudioExtensibility i zainstaluj pakiet NuGet.  
  
4.  Teraz możesz uruchomić VSIXSignTool z lokalizacji lokalnego pakietów projektu. Zapoznaj się z pomocą wiersza polecenia narzędzia podpisywania scenariusza (VSIXSignTool.exe /?).  
  
 Na przykład aby podpisać plik certyfikatu chronione hasłem:  
  
 /F znak VSIXSignTool.exe \<plik_certyfikatu > /p \<hasło > \<VSIXfile >  
  
## <a name="see-also"></a>Zobacz też  
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)