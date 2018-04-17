---
title: ClickOnce i ustawienia aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 69563869fe6518d112273da13889fc04db96d09f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="clickonce-and-application-settings"></a>ClickOnce i ustawienia aplikacji
Ustawienia aplikacji dla formularzy systemu Windows można łatwo tworzyć, przechowywać i Obsługa niestandardowych aplikacji i preferencji użytkownika na komputerze klienckim. Dokument zawiera informacje, jak działają pliki ustawień aplikacji w aplikacji ClickOnce, i jak ClickOnce wykonuje migrację ustawień, po uaktualnieniu do nowej wersji.  
  
 Poniższe informacje dotyczą tylko domyślny dostawca ustawień aplikacji, <xref:System.Configuration.LocalFileSettingsProvider> klasy. Jeśli podasz niestandardowego dostawcy, tego dostawcy określi, jak są przechowywane jego dane i jak uaktualni ona jego ustawienia między wersjami. Aby uzyskać więcej informacji o dostawcy ustawienia aplikacji, zobacz [Architektura ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>Pliki ustawień aplikacji  
 Ustawienia aplikacji wykorzystuje dwa pliki: *aplikacji*. exe.config i user.config, gdzie *aplikacji* to nazwa Twojej aplikacji formularzy systemu Windows. User.config jest tworzony na czas klienta pierwsza aplikacja przechowuje ustawienia zakresu użytkownika. *Aplikacja*. exe.config, natomiast będą istnieć przed ich wdrożeniem w przypadku definiowania wartości domyślne ustawień. Visual Studio będzie zawierać ten plik automatycznie korzystając z jego **publikowania** polecenia. Jeśli tworzysz aplikację ClickOnce za pomocą Mage.exe lub MageUI.exe, należy się upewnić, ten plik jest dołączony do aplikacji przez inne pliki podczas wypełniania manifest aplikacji.  
  
 W aplikacjach formularzy systemu Windows, nie wdrożone za pomocą aplikacji ClickOnce, aplikacja firmy *aplikacji*. exe.config plik jest przechowywany w katalogu aplikacji, podczas gdy plików user.config są przechowywane w użytkownika **dokumenty i ustawienia**  folderu. W aplikacji ClickOnce *aplikacji*. exe.config znajduje się w katalogu aplikacji w pamięci podręcznej aplikacji ClickOnce i user.config znajduje się w katalogu danych ClickOnce dla tej aplikacji.  
  
 Niezależnie od tego, jak w przypadku wdrażania aplikacji, ustawienia aplikacji zapewnia bezpieczne dostęp do odczytu do *aplikacji*. exe.config i bezpieczne odczytu i zapisu do user.config.  
  
 W aplikacji ClickOnce rozmiar pliki konfiguracji używane przez ustawienia aplikacji jest ograniczona przez rozmiar pamięci podręcznej ClickOnce. Aby uzyskać więcej informacji, zobacz [Przegląd pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Uaktualnienia wersji  
 Tak samo, jak każdej wersji aplikacji ClickOnce jest odizolowany od innych wersji, ustawienia aplikacji dla aplikacji ClickOnce są odizolowane od ustawień innych wersjach. Podczas uaktualniania użytkownika do nowszej wersji aplikacji, ustawienia aplikacji porównuje ustawień najnowszych (najwyższym numerze) wersji względem ustawienia dostarczony wraz z zaktualizowaną wersję i scaleń ustawień do nowego zestawu plików ustawień.  
  
 W poniższej tabeli opisano, jak ustawienia aplikacji decyduje o tym, które ustawienia do skopiowania.  
  
|Typ zmiany|Uaktualnij akcji|  
|--------------------|--------------------|  
|Ustawienie dodane do *aplikacji*. exe.config|Nowe ustawienie jest scalany bieżącej wersji *aplikacji*. exe.config|  
|Ustawienie usunięte z *aplikacji*. exe.config|Stare ustawienie zostanie usunięte z bieżącej wersji *aplikacji*. exe.config|  
|Domyślne ustawienia zostały zmienione; lokalne nadal ustawienie oryginalnych wartości domyślnych w user.config|Ustawienie jest scalany user.config bieżącej wersji z nowym domyślnym jako wartość|  
|Domyślne ustawienia zostały zmienione; Ustawienie wartości niedomyślnej w user.config|Ustawienie jest scalany user.config bieżącej wersji o wartości innej niż domyślna zachowane|  
  
 Jeśli utworzono ustawienia aplikacji klasy otoki i chcą dostosować logika aktualizacji, można zastąpić <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metody.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce i ustawienia roamingu  
 ClickOnce nie działa z ustawieniami roamingu, dzięki czemu plik ustawień do wykonania należy na komputerach w sieci. Jeśli potrzebujesz ustawienia roamingu, należy zaimplementować dostawcę ustawienia aplikacji, który przechowuje ustawienia za pośrednictwem sieci, lub opracowanie własnych klas niestandardowych ustawień do przechowywania ustawień na komputerze zdalnym. Aby uzyskać więcej informacji w dostawców ustawień, zobacz [Architektura ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Przegląd ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [Przegląd pamięci podręcznej w technologii ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)