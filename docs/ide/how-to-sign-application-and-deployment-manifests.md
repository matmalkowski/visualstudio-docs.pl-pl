---
title: 'Porady: podpisania manifestów aplikacji i wdrażania'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cee4f7ff8438c1e20f39a24e9e439e7507d655b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31951729"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Porady: podpisania manifestów aplikacji i wdrażania

Jeśli chcesz opublikować aplikację przy użyciu wdrażania ClickOnce, manifestów aplikacji i wdrażania muszą być podpisane przy użyciu pary kluczy publiczny/prywatny i podpisany przy użyciu technologii Authenticode. Można podpisać manifestów przy użyciu certyfikatu z magazynu certyfikatów systemu Windows lub pliku klucza.

 Aby uzyskać więcej informacji dotyczących wdrażania ClickOnce, zobacz [ClickOnce zabezpieczeń i wdrażania](../deployment/clickonce-security-and-deployment.md).

 Podpisywanie manifestów ClickOnce jest opcjonalne dla *.exe*— na podstawie aplikacji. Aby uzyskać więcej informacji zobacz sekcję "Generuj manifestów bez znaku" tego dokumentu.

 Aby uzyskać informacje o tworzeniu plików kluczy, zobacz [porady: tworzenie pary kluczy publiczno prywatnych](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] obsługuje tylko te klucza pliki wymiany informacji osobistych (PFX), które mają *PFX* rozszerzenia. Jednak można wybrać inne typy certyfikatów z magazynu certyfikatów bieżącego użytkownika systemu Windows, klikając **wybierz z magazynu** na **podpisywanie** strony właściwości projektu.

## <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>Do podpisania aplikacji i wdrażania manifesty przy użyciu certyfikatu

1.  Przejdź do okna właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**, lub typ **właściwości projektu** w **Szybkie uruchamianie** okna lub naciśnij przycisk **Alt**+**Enter** wewnątrz **Eksploratora rozwiązań** okno). Na **podpisywanie** wybierz opcję **podpisania manifestów ClickOnce** pole wyboru.

2.  Kliknij przycisk **wybierz z magazynu** przycisku.

     **Wybierz certyfikat** zostanie wyświetlone okno dialogowe i wyświetla zawartość magazynu certyfikatów systemu Windows.

    > [!TIP]
    > Jeśli klikniesz przycisk **kliknij tutaj, aby wyświetlić właściwości certyfikatu**, **szczegóły certyfikatu** zostanie wyświetlone okno dialogowe. To okno dialogowe zawiera szczegółowe informacje o certyfikacie i zawierają dodatkowe opcje. Możesz kliknąć **certyfikaty** Aby wyświetlić dodatkowe informacje.

3.  Wybierz certyfikat, który ma być używany do podpisywania manifestów.

4.  Ponadto można określić adres serwera sygnatury czasowej w **adres URL serwera znaczników czasu** pola tekstowego. Jest to serwer, który zapewnia sygnaturę określenia po podpisaniu manifestu.

## <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>Do podpisania aplikacji i wdrażania manifesty przy użyciu istniejącego pliku klucza

1.  Na **podpisywanie** wybierz pozycję **podpisania manifestów ClickOnce** pole wyboru.

2.  Kliknij przycisk **wybierz z pliku** przycisku.

     **Wybierz plik** zostanie wyświetlone okno dialogowe.

3.  W **wybierz plik** okno dialogowe, przejdź do lokalizacji pliku klucza (*PFX*), który chcesz użyć, a następnie kliknij przycisk **Otwórz**.

    > [!NOTE]
    > Ta opcja obsługuje tylko pliki mające *PFX* rozszerzenia. Jeśli masz plik klucza lub certyfikat w innym formacie, zapisz go w magazynie certyfikatów systemu Windows i wybierz certyfikat jest opisane w poprzedniej procedurze. Cel wybranego certyfikatu powinien zawierać podpisywania kodu.

     **Wprowadź hasło, aby otworzyć plik** zostanie wyświetlone okno dialogowe. (Jeśli *PFX* plik jest już przechowywany w magazynie certyfikatów systemu Windows lub nie jest chroniony hasłem, nie będzie zostanie monit o wprowadzenie hasła.)

4.  Wprowadź hasło, aby uzyskać dostęp do pliku klucza i naciśnij klawisz **Enter**.

## <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>Do podpisania aplikacji i wdrażania manifesty przy użyciu certyfikatu testowego

1.  Na **podpisywanie** wybierz pozycję **podpisania manifestów ClickOnce** pole wyboru.

2.  Aby utworzyć nowy certyfikat do testowania, kliknij przycisk **Tworzenie certyfikatu testowego** przycisku.

3.  W **utworzyć certyfikatu testu** okna dialogowego wprowadź hasło, aby pomóc w zabezpieczeniu certyfikatu testowego.

## <a name="generate-unsigned-manifests"></a>Generowanie manifestów bez znaku

Podpisywanie manifestów ClickOnce jest opcjonalne dla *.exe*— na podstawie aplikacji. W poniższych procedurach przedstawiono sposób generowania niepodpisane manifestów ClickOnce.

> [!IMPORTANT]
> Manifesty niepodpisane uprościć projektowania i testowania aplikacji. Jednak manifestów bez znaku powodować znaczne zagrożenia bezpieczeństwa w środowisku produkcyjnym. Tylko należy wziąć pod uwagę przy użyciu manifestów bez znaku, gdy aplikacja ClickOnce działa na komputerach w sieci intranet, które są całkowicie odizolowane od Internetu lub innych źródeł złośliwego kodu.

 Domyślnie ClickOnce automatycznie generuje podpisanych manifestów, chyba że jeden lub więcej plików w szczególności są wykluczone z wygenerowanym wyznaczania wartości skrótu. Innymi słowy, publikowanie wyników aplikacji w podpisanych manifestów, jeśli wszystkie pliki znajdują się w skrót, nawet wtedy, gdy **podpisania manifestów ClickOnce** pole wyboru jest wyczyszczone.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Aby wygenerować manifestów bez znaku i Dołącz wszystkie pliki zawarte w wygenerowanym wyznaczania wartości skrótu

1.  Aby wygenerować niepodpisanych manifestów, które obejmują wszystkie pliki w skrót, należy najpierw opublikować aplikacji wraz z podpisanych manifestów. W związku z tym najpierw podpisania manifestów ClickOnce przez następujące poprzedniej procedury, a następnie Opublikuj aplikację.

2.  Na **podpisywanie** wyczyść **podpisania manifestów ClickOnce** pole wyboru.

3.  Zresetowanie wersji publikacji, tak że tylko jedna wersja aplikacji jest dostępna. Domyślnie program Visual Studio automatycznie zwiększa numer poprawki wersji publikacji zawsze po opublikowaniu aplikacji. Aby uzyskać więcej informacji, zobacz [porady: wersji publikacji ClickOnce zestawu](../deployment/how-to-set-the-clickonce-publish-version.md).

4.  Publikowanie aplikacji.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Aby wygenerować manifestów bez znaku i wykluczyć jeden lub więcej plików z wygenerowanym wyznaczania wartości skrótu

1.  Na **podpisywanie** wyczyść **podpisania manifestów ClickOnce** pole wyboru.

2.  Otwórz **pliki aplikacji** okno dialogowe i zestaw **skrótu** do **wykluczyć** dla plików, które chcesz wykluczyć z wygenerowanym wyznaczania wartości skrótu.

    > [!NOTE]
    > Wykluczanie pliku skrót konfiguruje ClickOnce, aby wyłączyć automatyczne podpisywania manifestów, dzięki czemu nie trzeba najpierw opublikować z podpisanych manifestów, jak pokazano w poprzedniej procedurze.

3.  Publikowanie aplikacji.

## <a name="see-also"></a>Zobacz także

- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)
- [Porady: tworzenie pary kluczy publiczno prywatnych](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md)
- [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)