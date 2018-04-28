---
title: Zarządzanie zestawu i manifestu podpisywania
ms.date: 02/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c06ffe38b0d269562c7315d54da8c4d0a99218f
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="manage-assembly-and-manifest-signing"></a>Zarządzanie zestawu i manifestu podpisywania

Podpisu silnej nazwy zawiera składnik oprogramowania unikatowych tożsamości. Silnych nazw są używane, aby zagwarantować, że zestaw nie może być sfałszowane przez kogoś innego i upewnij się, że składnik zależności i instrukcje konfiguracji mapowania na składnik prawidłowa, a wersja składnika.

 Silnej nazwy składa się z tożsamości zestawu (zwykły tekst nazwa, numer wersji i informacje o ustawieniach kulturowych) oraz token klucza publicznego i podpis cyfrowy.

 Aby uzyskać informacje dotyczące podpisywania zestawów w projektach Visual Basic i C#, zobacz [tworzenie i używanie zestawów o silnych nazwach](http://msdn.microsoft.com/Library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

 Aby uzyskać informacji na temat podpisywania zestawów w projektach Visual C++, zobacz [silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Podpisu silnej nazwy nie chroni przed odtwarzania zestawu.  Aby zapewnić ochronę przed odtwarzania, zobacz [Dotfuscator Community Edition (CE)](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Typy zasobów i podpisywania

Możesz zarejestrować zestawów platformy .NET i manifestów aplikacji. Należą do nich między innymi:

-   pliki wykonywalne (*.exe*)

-   Manifesty aplikacji (*. exe.manifest*)

-   manifesty wdrożenia (*.application*)

-   udostępnionych zestawów składników (*.dll*)

Musisz zalogować się następujące typy zasobów:

1.  Zestawy, jeśli chcesz wdrożyć je w globalnej pamięci podręcznej zestawów (GAC).

2.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifesty aplikacji i wdrażania. Program Visual Studio pozwala podpisywania domyślnie dla tych aplikacji.

3.  Podstawowe zestawy międzyoperacyjne, które są używane do współdziałania COM. Narzędzia TLBIMP wymusza silne nazwy podczas tworzenia podstawowego zestawu międzyoperacyjnego z biblioteki typów COM.

Ogólnie rzecz biorąc nie podpisuj plików wykonywalnych. Składnik silnej nazwy nie może odwoływać się z systemem innym niż-o silnej nazwie składnika, które zostało wdrożone w aplikacji. Program Visual Studio nie podpisać pliki wykonywalne aplikacji, ale zamiast tego podpisuje manifest aplikacji, wskazujący do pliku wykonywalnego o nazwie niska. Ogólnie należy unikać podpisywania składników, które są prywatne do aplikacji, ponieważ podpisywanie może utrudnić zarządzanie zależności.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Sposób podpisywania zestawu w programie Visual Studio

Zarejestrować aplikację lub składnik przy użyciu **podpisywanie** karcie okna właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**, lub typ **właściwości projektu** w **Szybkie uruchamianie** okna lub naciśnij przycisk **Alt**+**Enter**wewnątrz **Eksploratora rozwiązań** okno). Wybierz **podpisywanie** , a następnie wybierz **Podpisz zestaw** pole wyboru.

Określ plik klucza. Jeśli wybierzesz opcję utworzenia nowego pliku klucza, należy pamiętać, że nowe pliki klucza są zawsze utworzony w *PFX* format. Należy nazwę i hasło dla nowego pliku.

> [!WARNING]
> Należy zawsze zabezpieczyć plik klucza przy użyciu hasła, aby zapobiec ktoś inny używa jej. Za pomocą dostawcy i magazyny certyfikatów, można zabezpieczyć klucze.

 Może także wskazywać do klucza, które zostały już utworzone. Aby uzyskać więcej informacji na temat tworzenia kluczy, zobacz [porady: tworzenie pary kluczy publiczno prywatnych](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

 Jeśli użytkownik ma dostęp tylko z kluczem publicznym, można użyć opóźnione podpisywanie, które mają być odroczone przypisywanie klucz. Włącz opóźnione podpisywanie wybierając **opóźnienie tylko znak** pole wyboru. Projekt jako podpisywany z opóźnieniem nie będzie działać, a nie można debugować go. Jednak można pominąć weryfikacji podczas tworzenia przy użyciu [Sn.exe (narzędzie silnych nazw)](/dotnet/framework/tools/sn-exe-strong-name-tool) z `-Vr` opcji.

 Aby uzyskać informacje na temat podpisywania manifestów, zobacz [porady: podpisania manifestów aplikacji i wdrażania](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Zobacz także

- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)
- [Silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
