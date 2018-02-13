---
title: Odinstalowanie programu Visual Studio for Mac | Dokumentacja firmy Microsoft
description: "Instrukcje dotyczące odinstalowywania programu Visual Studio dla komputerów Mac oraz narzędzia pokrewne."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 193856ca96395db9a5b3bd494a5b8f1f7331f702
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2018
---
# <a name="uninstalling-visual-studio-for-mac"></a>Odinstalowanie programu Visual Studio dla komputerów Mac

Istnieje wiele produktów Xamarin, które umożliwiają tworzenie aplikacji wieloplatformowych, tym autonomicznej aplikacji, takich jak Visual Studio dla komputerów Mac.

Ten przewodnik może służyć do odinstalowania każdego produktu pojedynczo, przechodząc do odpowiedniej sekcji. Cały zestaw narzędzi platformy Xamarin można odinstalować czynności przedstawione w tym przewodniku aż.

Jeśli wcześniej wystąpiły Xamarin Studio na komputerze jest zainstalowany, może być również konieczne postępuj zgodnie z instrukcjami w [odinstalować](https://developer.xamarin.com/guides/cross-platform/getting_started/installation/uninstalling_xamarin/) na developer.xamarin.com, także do przewodnika następujące kroki.

## <a name="uninstall-script"></a>Odinstaluj skryptu

Należy odinstalować program Visual Studio i związanych z nimi elementów w jednym go za pomocą [odinstalować skryptu](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Ten skrypt dezinstalacji skryptu zawiera większość potrzebnych poleceń, które można znaleźć w artykule. Istnieją dwa główne pominięć skryptu i nie są uwzględniane z powodu możliwych zależności zewnętrznych:

- **Odinstalowywanie Mono**
- **Odinstalowywanie AVD systemu Android**

Aby uruchomić skrypt, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy na skrypt i wybierz **Zapisz jako...** Aby zapisać plik opartym na systemie
2. Otwórz Terminal i zmień katalog roboczy, do której pobrano skrypt:

    ```bash
    $ cd /location/of/file
    ```
3. Wykonywalny skrypt i uruchom go z **sudo**:

    ```bash
    $ chmod +x ./uninstall-vsmac.sh
    $ sudo ./uninstall-vsmac.sh
    ```
4. Na koniec usunąć skrypt dezinstalacji skryptu.

## <a name="uninstall-visual-studio-for-mac"></a>Odinstaluj program Visual Studio dla komputerów Mac

Pierwszym krokiem podczas odinstalowywania programu Visual Studio z Mac jest zlokalizowanie **Visual Studio.app** w **/Applications** katalogu i przeciągnij go do **Kosz**. Alternatywnie kliknij prawym przyciskiem myszy i wybierz **Przenieś do Kosza** jak pokazano na poniższej ilustracji:

![Aplikacji programu Visual Studio Przenieś do Kosza](media/uninstall-image1.png)

Usunięcie tego pakietu aplikacji spowoduje usunięcie programu Visual Studio dla komputerów Mac, nawet jeśli mogą istnieć inne pliki odnoszących się do platformy Xamarin nadal w systemie plików.

Usuń wszystkie ślady programu Visual Studio for Mac, następujące polecenia powinna być uruchamiana w terminalu:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Developer/Xamarin
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

## <a name="uninstall-mono-sdk-mdk"></a>Odinstaluj zestaw SDK Mono (MDK)

Mono jest implementacją open source firmy Microsoft .NET Framework i umożliwia Products—Xamarin.iOS platformy Xamarin.IOS, Xamarin.Android i Xamarin.Mac rozwój tych platform w języku C#.

> [!WARNING]
> Istnieją inne aplikacje w zakresie poza Visual Studio dla komputerów Mac, które także używają Mono, takich jak Unity.
> Pamiętaj, że nie ma żadnych innych zależności na Mono przed jego odinstalowaniem.

Aby usunąć Mono Framework z komputera, uruchom następujące polecenia w terminalu:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Uninstall Xamarin.Android

Istnieje wiele elementów wymaganych do instalacji i korzystania z platformy Xamarin.Android, takich jak zestaw SDK systemu Android i zestawu Java SDK.

Aby usunąć Xamarin.Android, użyj następujących poleceń:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Odinstaluj zestaw SDK systemu Android SDK i Java

Zestaw SDK systemu Android jest wymagany dla opracowywania aplikacji systemu Android. Aby całkowicie usunąć wszystkie części zestawu SDK systemu Android, zlokalizuj plik na **~/Library/Developer/Xamarin/** i przenieść ją do **Kosza**.

Zestaw SDK Java (JDK) nie musi ma zostać odinstalowany, ponieważ już jest wstępnie dostarczana jako część systemu Mac OS X / macOS.

### <a name="uninstall-android-avd"></a>Odinstaluj AVD systemu Android

> [!WARNING]
> Istnieją inne aplikacje w zakresie poza Visual Studio for Mac, które także używają Android AVD i te dodatkowe składniki systemu android, takie jak Android Studio.
> Usunięcie tego katalogu może spowodować projekty można przerwać w programie Android Studio. 

Aby usunąć wszelkie Android urządzeń Avd i Android dodatkowe składniki, użyj następującego polecenia:

```bash
rm -rf ~/.android
```

Aby usunąć tylko Android urządzeń Avd, użyj następującego polecenia:

```bash
rm -rf ~/.android/avd
```

 

## <a name="uninstall-xamarinios"></a>Odinstalowywanie platformy Xamarin.iOS

Xamarin.iOS umożliwia iOS projektowanie aplikacji przy użyciu języka C# lub języka F # za pomocą programu Visual Studio dla komputerów Mac.

Użyj następujących poleceń w terminalu, aby usunąć wszystkie pliki Xamarin.iOS z systemu plików:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Uninstall Xamarin.Mac

Xamarin.Mac może zostać usunięty z komputera, odpowiednio likwidacji produktu i licencji z komputera Mac przy użyciu dwóch następujących poleceń:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Odinstaluj skoroszyty i Inspektora

Począwszy od 1.2.2 skoroszyty Xamarin & Inspektor mogła zostać usunięta z terminalu, uruchamiając:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Dla starszych wersji należy ręcznie usunąć następujące artefakty:

* Usuń aplikację skoroszytów w`"/Applications/Xamarin Workbooks.app"`
* Usuń aplikację inspektora w`"Applications/Xamarin Inspector.app"`
* Usuń dodatki: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` i`"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Usuń inspektora i tutaj plików pomocniczych: `/Library/Frameworks/Xamarin.Interactive.framework` i`/Library/Frameworks/Xamarin.Inspector.framework`

# <a name="uninstall-the-xamarin-profiler"></a>Odinstalowanie programu Xamarin

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Odinstaluj Instalator programu Visual Studio

Aby usunąć wszystkie ślady Instalator uniwersalnych platformy Xamarin, użyj następujących poleceń:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```
