---
title: "Proces instalacji programu Visual Studio przy użyciu pliku odpowiedzi | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak utworzyć plik odpowiedzi JSON, który pomaga zautomatyzować instalację programu Visual Studio"
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: timsneath
ms.author: tglee
manager: ghogen
ms.openlocfilehash: f8103f1d160370853e461288010e434095c776c2
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-define-settings-in-a-response-file"></a>Sposób definiowania ustawień w pliku odpowiedzi
Administratorzy, którzy wdrażają Visual Studio można określić plik odpowiedzi przy użyciu `--in` parametru, jak w poniższym przykładzie:

```
vs_enterprise.exe --in customInstall.json
```

Pliki odpowiedzi są [JSON](http://json-schema.org/) pliki, których zawartość duplikatów argumenty wiersza polecenia.  Ogólnie, jeśli parametr wiersza polecenia nie przyjmuje żadnych argumentów (na przykład `--quiet`, `--passive`, itd.), wartość w pliku odpowiedzi powinna być PRAWDA/FAŁSZ.  Jeśli trwa argumentu (na przykład `--installPath <dir>`), wartość w pliku odpowiedzi musi być ciągiem.  Jeśli używa argumentu i może występować więcej niż raz w wierszu polecenia (na przykład `--add <id>`), należy go, tablicy ciągów.

Parametry, które są określone na ustawienia wiersza polecenia zastąpienia z pliku odpowiedzi, z wyjątkiem, gdy parametry podjęcia wielu danych wejściowych (na przykład `--add`). Jeśli masz wielu danych wejściowych wejścia podana w wierszu polecenia są łączone przy użyciu ustawień z pliku odpowiedzi.

# <a name="setting-a-default-configuration-for-visual-studio"></a>Ustawienie konfiguracji domyślnej dla programu Visual Studio

Jeśli utworzono sieci układu pamięci podręcznej z `--layout`, początkowego `response.json` plik jest tworzony w układzie. W przypadku utworzenia układu częściowe, ten plik odpowiedzi zawiera obciążeń i języki, które zostały uwzględnione w układzie.  Automatycznie uruchomić Instalatora z tego układu używa tego pliku response.json, który wybiera obciążeń i składników zawartych w układzie.  Użytkownicy nadal można zaznacz lub odznacz wszystkie obciążenia w konfiguracji interfejsu użytkownika przed zainstalowaniem programu Visual Studio.

Administratorzy, którzy tworzenie układu można zmodyfikować `response.json` w układzie do kontrolowania ustawień domyślnych, że ich użytkownicy będą widzieć podczas instalacji programu Visual Studio z układu.  Na przykład, jeśli administrator chce konkretnych obciążeń i składniki instalowane domyślnie, można skonfigurować `response.json` plik, aby dodać je.

Po uruchomieniu Instalatora programu Visual Studio z folderem układu go _automatycznie_ używa pliku odpowiedzi w folderze układu.  Nie trzeba używać `--in` opcji.

Można aktualizować `response.json` pliku, który jest tworzony w folderze układu w trybie offline, aby zdefiniować domyślne ustawienie dla użytkowników, którzy instalują z tego układu.

> [!WARNING]
> Jest krytyczne pozostawienie istniejącej właściwości, które zostały określone podczas tworzenia układu.

Podstawowym `response.json` pliku w układzie powinien wyglądać podobnie do poniższego przykładu z tą różnicą, że będzie zawierać wartość dla produktu i kanał, który ma zostać zainstalowany:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```
Podczas tworzenia lub aktualizowania układ, tworzona jest również plik response.template.json.  Ten plik zawiera wszystkie obciążenia, składników i języka identyfikatorów, które mogą być używane.  Ten plik jest dostarczany, ponieważ szablon dla wszystkich, jakie można uwzględniony w instalacji niestandardowej.  Administratorzy mogą używać tego pliku jako punkt początkowy dla pliku odpowiedzi niestandardowych.  Po prostu usuń identyfikatorów czynności, które chcesz zainstalować i zapisz go w pliku odpowiedzi.  Nie dostosować plik response.template.json lub zmiany zostaną utracone przy każdej aktualizacji układu.

## <a name="example-layout-response-file-content"></a>Zawartość pliku odpowiedzi układu przykład
W poniższym przykładzie instalowana Visual Studio Enterprise z sześciu typowych obciążeń i składników oraz zarówno angielskim i francuskim interfejsu użytkownika. W tym przykładzie można użyć jako szablonu; można zmienić obciążeń i składniki do tych, które chcesz zainstalować:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) stronę porady dotyczące rozwiązywania problemów. Jak również zgłosić problemy produktu z nami za pośrednictwem [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia w programie Visual Studio IDE lub udział sugestia z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579). Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi. Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio) (wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także
* [Visual Studio 2017 obciążenia i składnik identyfikatorów](workload-and-component-ids.md)
