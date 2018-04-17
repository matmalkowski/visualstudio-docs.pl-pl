---
title: Implementowanie niestandardowych kategorii i Wyświetl elementy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9593a7addcd9a3f100f45f69e7e692c396e33bfe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementowanie niestandardowych kategorii i wyświetlania elementów
Pakiet VSPackage zapewnia kontrolę nad czcionki i kolory jego tekstu do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) za pomocą niestandardowych kategorii i wyświetlania elementów.

 Niestandardowe kategorie i Wyświetl elementy znajdują się na **czcionki i kolory** strony właściwości. Aby otworzyć **czcionki i kolory** na stronie właściwości **narzędzia** menu, kliknij przycisk **opcje**. Rozwiń węzeł **środowiska** , a następnie kliknij przycisk **czcionki i kolory**.

 Korzystając z tego mechanizmu, musi implementować VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu i skojarzone interfejsy.

 W zasadzie mechanizm ten może służyć do modyfikowania wszystkich istniejących **wyświetlania elementów** i **kategorii** zawierające je. Jednak nie można stosować do modyfikowania **EditorCategory tekst** lub jego **wyświetlania elementów**. Aby uzyskać więcej informacji, zobacz [Omówienie kolorów i czcionek](../extensibility/font-and-color-overview.md).

 Aby wdrożyć niestandardowy **kategorii** lub **wyświetlania elementów**, pakiet VSPackage musi:

-   Tworzenie lub identyfikowanie kategorii w rejestrze.

     Implementacja programu IDE **czcionki i kolory** strony właściwości używa tych informacji do poprawnie kwerendy usługi obsługujące danej kategorii.

-   Tworzenie lub identyfikowanie grupy (opcjonalnie) w rejestrze.

     Może to być przydatne do zdefiniowania grupy, która reprezentuje sumę dwóch lub więcej kategorii. Jeśli zdefiniowano grupy, IDE automatycznie scala podkategorie i dystrybuuje wyświetlania elementów w obrębie grupy.

-   Implementuje Obsługa środowiska IDE.

-   Obsługa zmiany czcionek i kolorów.

 Aby uzyskać informacje, zobacz [podczas uzyskiwania dostępu do przechowywanych czcionkę i ustawienia koloru](../extensibility/accessing-stored-font-and-color-settings.md).

## <a name="to-create-or-identify-categories"></a>Aby utworzyć lub wskazać kategorii

-   Utworzyć specjalny typ wpisu rejestru kategorii [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<wersji programu Visual Studio >*\FontAndColors\\`<Category>`]

     *\<Kategoria >* niezlokalizowana nazwa kategorii.

-   Wypełnij rejestru z dwóch wartości:

    |Nazwa|Typ|Dane|Opis|
    |----------|----------|----------|-----------------|
    |Kategoria|REG_SZ|Identyfikator GUID|Identyfikator GUID utworzone w celu identyfikacji kategorii.|
    |Package|REG_SZ|Identyfikator GUID|Identyfikator GUID usługi pakiet VSPackage, która obsługuje kategorii.|

 Usługi określonego w rejestrze musi zapewniać implementację elementu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> odpowiedniej kategorii.

## <a name="to-create-or-identify-groups"></a>Aby utworzyć lub wskazać grupy

-   Utworzyć specjalny typ wpisu rejestru kategorii [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<wersji programu Visual Studio >*\FontAndColors\\  *\<grupy >*]

     *\<grupy >* niezlokalizowana Nazwa grupy.

-   Wypełnij rejestru z dwóch wartości:

    |Nazwa|Typ|Dane|Opis|
    |----------|----------|----------|-----------------|
    |Kategoria|REG_SZ|Identyfikator GUID|Identyfikator GUID utworzone, aby zidentyfikować grupę.|
    |Package|REG_SZ|Identyfikator GUID|Identyfikator GUID usługi, która obsługuje kategorii.|

 Usługi określonego w rejestrze musi zapewniać implementację elementu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> dla odpowiedniej grupy.

## <a name="to-implement-ide-support"></a>Obsługa środowiska IDE

-   Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, który zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfejsu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu IDE dla każdego **kategorii** lub grupy z podanym identyfikatorem GUID.

-   Dla każdego **kategorii** obsługuje, pakiet VSPackage implementuje oddzielnego wystąpienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfejsu.

-   Metody implementowane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> podać IDE z:

    -   Wykaz **wyświetlania elementów** w **kategorii.**

    -   Nazwy Lokalizowalny **wyświetlania elementów**.

    -   Wyświetl informacje o każdym członku **kategorii**.

    > [!NOTE]
    >  Każdy **kategorii** musi zawierać co najmniej jeden **wyświetlanego elementu**.

-   Używa IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu, aby zdefiniować związku kilka kategorii.

     Jego wdrożenie zapewnia IDE z:

    -   Lista **kategorii** wchodzące w skład danej grupie.

    -   Dostęp do wystąpień <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> obsługi każdego **kategorii** w obrębie grupy.

    -   Nazwy grup lokalizowalny.

-   Aktualizowanie IDE:

     IDE przechowuje informacje o **czcionek i kolorów** ustawienia. W związku z tym po wszelkich zmianach IDE **czcionek i kolorów** konfiguracji, zaleca się upewnić, że pamięć podręczna jest aktualna.

 Aktualizacja pamięci podręcznej odbywa się za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejsu i mogą być wykonywane globalnie lub tylko na wybranych elementów.

## <a name="to-handle-font-and-color-changes"></a>Aby obsługiwać czcionek i kolorów zmian
 Aby poprawnie obsługiwać kolorowania tekstu, który zawiera pakiet VSPackage, usługa kolorowania obsługujący pakiet VSPackage musi odpowiadać na zainicjowane przez użytkownika zmiany wprowadzane za pośrednictwem **czcionki i kolory** stronę właściwości. Pakiet VSPackage następującym cechom:

-   Obsługa zdarzeń generowanych przez IDE zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfejsu.

     IDE wywołuje odpowiednią metodę po modyfikacji użytkownika **czcionki i kolory** strony. Na przykład wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> metodę, jeśli wybrano nowej czcionki.

     —lub—

-   Sondowanie w IDE dla zmian.

     Można to zrobić za pomocą systemu zaimplementowana <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu. Mimo że przede wszystkim dotyczące obsługi trwałości, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> — metoda pozwala uzyskać informacje dotyczące czcionek i kolorów **wyświetlania elementów**. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do przechowywanych czcionkę i ustawienia koloru](../extensibility/accessing-stored-font-and-color-settings.md).

    > [!NOTE]
    >  Aby upewnić się, że wyniki uzyskane za pomocą sondowania są poprawne, warto użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejs do ustalenia, czy czyszczenie pamięci podręcznej i aktualizacji są potrzebne przed wywołaniem metody pobierania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [Pobieranie czcionek i kolorów informacje dotyczące tekstu kolorowania](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Dostęp do przechowywanej czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md)
- [Porady: dostęp do wbudowanych czcionek i schemat kolorów](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [Omówienie kolorów i czcionek](../extensibility/font-and-color-overview.md)