---
title: Zarządzanie podpisywaniem zestawu i manifestu
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
ms.openlocfilehash: fb2113ed091d99ed66b13955ea468c376bba9490
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379569"
---
# <a name="manage-assembly-and-manifest-signing"></a>Zarządzanie podpisywaniem zestawu i manifestu

Podpisywania silnymi zawiera składnik oprogramowania globalnie unikatową tożsamość. Silne nazwy są używane w celu zagwarantowania, że zestaw nie sfałszowane przez kogoś innego i upewnij się, że składnika, zależności i instrukcji konfiguracji mapowania na poprawne składnik, a wersja składnika.

Silna nazwa składa się z tożsamości zestawu (nazwa prosty tekst, numeru wersji i informacji o kulturze) oraz token klucza publicznego i podpisu cyfrowego.

Aby uzyskać informacje na temat podpisywania zestawów w projektach Visual Basic i C#, zobacz [tworzenia i używania zestawów o silnych nazwach](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Aby uzyskać informacji na temat podpisywania zestawów w projektach języka Visual C++, zobacz [zestawy o silnych nazwach (C + +/ CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Podpisywanie silnej nazwy nie chroni przed odtwarzania zestaw. Aby zapewnić ochronę przed odtwarzania, zobacz [Dotfuscator Community Edition (CE)](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Typy zasobów i podpisywania

Można podpisać manifesty aplikacji i zestawy .NET:

- Pliki wykonywalne (*.exe*)

- Manifesty aplikacji (*. exe.manifest*)

- Manifesty wdrożenia (*.application*)

- Współużytkowane zestawy składników (*.dll*)

Utwórz następujące typy zasobów:

1. Zestawy, jeśli chcesz wdrożyć je w globalnej pamięci podręcznej zestawów (GAC).

2. Manifesty aplikacji i wdrażania ClickOnce. Program Visual Studio umożliwia podpisywania domyślnie w przypadku tych aplikacji.

3. Podstawowe zestawy międzyoperacyjne, które są używane do współdziałania COM. Narzędzia TLBIMP wymusza silne nazwy podczas tworzenia podstawowego zestawu międzyoperacyjnego z biblioteki typów COM.

Ogólnie rzecz biorąc nie powinien utworzyć pliki wykonywalne. Składnik silnej nazwy nie mogą odwoływać się bez — nazwie składnik wdrożoną wraz z aplikacją. Visual Studio nie podpisuje plików wykonywalnych aplikacji, ale zamiast tego podpisuje manifest aplikacji, które wskazuje do pliku wykonywalnego o nazwie weak. Należy unikać podpisywania składników, które są prywatne do aplikacji, ponieważ podpisywanie może utrudnić zarządzanie zależnościami.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Jak zarejestrować zestaw w programie Visual Studio

Podpisywania aplikacji lub składnika przy użyciu **podpisywanie** karty w oknie właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**, lub typu **właściwości projektu** w **Szybkie uruchamianie** okna lub naciśnij klawisz **Alt**+**Enter** wewnątrz **Eksploratora rozwiązań**). Wybierz **podpisywanie** kartę, a następnie wybierz **Podpisz zestaw** pole wyboru.

Określ plik klucza. Jeśli zdecydujesz się utworzyć nowy plik klucza, nowe pliki klucza są zawsze tworzone w *PFX* formatu. Należy nazwę i hasło dla nowego pliku.

> [!WARNING]
> Zawsze należy chronić Twojego pliku klucza o hasło, aby uniemożliwić korzystanie z jej przez kogoś innego. Możesz również klucze można zabezpieczyć przy użyciu dostawców lub magazynów certyfikatów.

Możesz też wskazać w kluczu już utworzony. Aby uzyskać więcej informacji na temat tworzenia kluczy, zobacz [tworzenia pary kluczy publiczny prywatny](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Jeśli masz tylko dostęp do klucza publicznego, służy podpisywanie opóźnione mają być odroczone przypisywanie klucza. Włączanie opóźnione podpisywanie, wybierając **opóźnienie logowania tylko** pole wyboru. Projekt podpisywane z opóźnieniem nie zostanie uruchomiona, a nie można go debugować. Jednakże, możesz pominąć weryfikacji podczas programowania przy użyciu [narzędzie silnych nazw Sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) z `-Vr` opcji.

Aby uzyskać informacje dotyczące podpisywania manifestów, zobacz [porady: podpisywanie manifestów aplikacji i wdrożenia](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Zobacz także

- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)
- [Zestawy o silnych nazwach (C + +/ CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
