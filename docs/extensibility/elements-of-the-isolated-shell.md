---
redirect_url: shell/elements-of-the-isolated-shell
title: Elementy programu Isolated Shell | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b1e52963253f73c633b9b14bf64525bdb0afaeab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-the-isolated-shell"></a>Elementy programu Isolated Shell
Można zmodyfikować ustawienia rejestru, ustawienia środowiska wykonawczego i punkt wejścia aplikacji w Twojej aplikacji isolated shell i jego vsct, .pkgdef, and.pkgundef plików.  
  
## <a name="registry-settings"></a>Ustawienia rejestru  
 Zarówno .pkgdef, jak i plików .pkgundef zmodyfikować ustawienia rejestru dla aplikacji isolated shell. Po uruchomieniu aplikacji, ustawień rejestru są zdefiniowane w następującej kolejności:  
  
 Po uruchomieniu aplikacji, ustawień rejestru są zdefiniowane w następującej kolejności:  
  
1.  Utworzenie klucza rejestru dla aplikacji.  
  
2.  Rejestru są aktualizowane na podstawie pliku .pkgdef aplikacji, definiując określone klucze i zapisów.  
  
3.  Dla każdego pakietu, który jest częścią aplikacji rejestru są aktualizowane na podstawie pliku .pkgdef tego pakietu. Każdy pakiet jest zdefiniowany w pliku .pkgdef aplikacji przez $RootKey$ \Packages\\{*vsPackageGuid*} klucza dla pakietu.  
  
4.  Rejestr są aktualizowane z AppEnvConfig.pkgdef i BaseConfig.pkgdef w *ścieżki instalacji programu Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform katalogu. Te pliki są częścią programu Visual Studio, a także częścią pakietu redystrybucyjnego programu Visual Studio Shell (tryb izolowany).  
  
5.  Rejestr są aktualizowane na podstawie pliku .pkgundef aplikacji przez usunięcie określone klucze i zapisów.  
  
## <a name="run-time-settings"></a>Ustawienia środowiska wykonawczego  
 Po uruchomieniu aplikacji isolated shell wywołuje punkt wejścia uruchamiania powłoki programu Visual Studio. Ustawienia aplikacji są zdefiniowane podczas uruchamiania aplikacji, w następujący sposób:  
  
1.  Visual Studio shell sprawdza dla określonych kluczy rejestru aplikacji. Jeśli ustawienie klucza jest określony w wywołaniu początkowy punkt wejścia, ta wartość zastępuje wartość w rejestrze.  
  
2.  Jeśli punkt wejścia ani rejestru parametr określa wartość ustawienia, a następnie zostanie użyta domyślna wartość ustawienia.  
  
 Gdy użytkownik uruchamia aplikację z poziomu wiersza polecenia, wszystkie przełączniki wiersza polecenia są przekazywane do powłoki programu Visual Studio, które je w taki sam sposób, który wykonuje Devenv. Aby uzyskać więcej informacji na temat parametrów Devenv zobacz [przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md) i [przełączniki wiersza polecenia Devenv dla rozwoju pakiet VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Aby uzyskać więcej informacji dotyczących sposobu pakietu rejestruje przełączniki wiersza polecenia, zobacz [Dodawanie przełączniki wiersza polecenia](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Początkowy punkt wejścia  
 Plik Appenvstub.dll zawiera punkty wejścia do uzyskiwania dostępu do programu isolated shell. Podczas uruchamiania aplikacji, wywołuje punkt wejścia Start Appenvstub.dll.  
  
 Sposób działania aplikacji można zmienić, zmieniając wartość ostatni parametr, który jest przekazywany do uruchomienia punktu wejścia. Aby uzyskać więcej informacji, zobacz [izolowane powłoki wpis punktu parametrów (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>. Plik Vsct  
 Pliku vsct umożliwia określenie, które standardowe elementy interfejsu użytkownika programu Visual Studio są dostępne w aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>. Plik Pkgundef  
 Gdy aplikacja jest zainstalowana na komputerze, na którym jest już zainstalowany program Visual Studio, kopię wpisy rejestru programu Visual Studio zostanie przeprowadzona dla aplikacji. Domyślnie aplikacja używa VSPackages, które są już zainstalowane na komputerze. Plik .pkgundef umożliwia wykluczenie wpisy rejestru w celu usuwania określonych elementów Visual Studio shell lub rozszerzeń z aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Plik .pkgundef umożliwia wykluczenie wpisy rejestru w celu usuwania określonych elementów Visual Studio shell lub rozszerzeń z aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Zestaw identyfikatorów GUID, które można wykluczyć pakietu są wymienione w [pakietu identyfikatorów GUID programu Visual Studio funkcji](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>. Pliku Pkgdef  
 Plik .pkgdef pozwala zdefiniować wpisy rejestru dla aplikacji, które są ustawione, gdy aplikacja jest zainstalowana. Opis pliku .pkgdef i listy wpisów rejestru, który korzysta z powłoki programu Visual Studio, zobacz [. Pliki Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Ciągi podstawienia  
 Ciągi podstawienia używany w plikach .pkgdef i .pkgundef są wymienione w [podstawienia ciągi używane w. Pkgdef i. Pliki Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Inne ustawienia  
 Jeśli aplikacja programu isolated shell zależy od Microsoft.VisualStudio.GraphModel.dll, należy dodać następujące przekierowania powiązania do pliku config aplikacji Isolated Shell:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```