---
title: Dostęp do przechowywanej czcionek i kolorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1280555a2b8a293fcdd0f86891a1d198ef3c99d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-stored-font-and-color-settings"></a>Dostęp do przechowywanej czcionek i kolorów
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE) przechowuje zmodyfikowane ustawienia czcionek i kolorów w rejestrze. Można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu uzyskać dostępu do tych ustawień.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Aby zainicjować stanu trwałości czcionek i kolorów
 Informacje o czcionek i kolorów są przechowywane według kategorii w następującej lokalizacji rejestru: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<wersji programu Visual Studio >*\FontAndColors\\  *\<CategoryGUID >*], gdzie  *\<CategoryGUID >* kategorii identyfikatora GUID.

 W związku z tym aby zainicjować trwałości, pakiet VSPackage musi:

-   Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu, wywołując `QueryService` względem dostawcy usług globalnych.

     `QueryService` musi zostać wywołana za pomocą argumentu identyfikator usługi `SID_SVsFontAndColorStorage` i argument Identyfikatora interfejsu `IID_IVsFontAndColorStorage`.

-   Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodę, aby otworzyć kategorię, aby trwale znajdować się przy użyciu identyfikatora GUID kategorii i flagę trybu jako argumenty.

     Określony przez tryb `fFlags` argumentu, jest tworzony z wartości w <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> wyliczenia. W tym trybie kontrolki:

    -   Ustawienia, które są dostępne za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.

    -   Wszystkie ustawienia lub tylko te ustawienia, które modyfikują użytkowników i do których można odzyskać <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.

    -   Sposób propagowanie zmian ustawień użytkownika.

    -   Format wartości kolorów, które są używane.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Aby użyć stanu trwałości czcionek i kolorów
 Utrwalanie czcionki i kolory obejmuje:

-   Synchronizowanie ustawień IDE z ustawień przechowywanych w rejestrze.

-   Propagowanie informacji modyfikacji rejestru.

-   Ustawianie i pobieranie ustawień przechowywanych w rejestrze.

 Synchronizacja ustawienia magazynu przy użyciu ustawień IDE to przede wszystkim przezroczysty. Podstawowy IDE automatycznie zapisuje zaktualizowano ustawienia dla **wyświetlania elementów** do wpisów rejestru kategorii.

 Wiele VSPackages udostępniania określonej kategorii, pakiet VSPackage należy wymagać generowane są zdarzenia, gdy metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu są używane do modyfikowania ustawień rejestru przechowywane.

 Generowanie zdarzeń nie jest włączona domyślnie. Aby włączyć generowanie zdarzeń, należy otworzyć kategorię przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Otwieranie kategorii spowoduje, że IDE wywołać odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metodę, która implementuje pakiet VSPackage.

> [!NOTE]
>  Modyfikacje za pośrednictwem **czcionek i kolorów** strony właściwości generowanie zdarzeń niezależnie od <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejs do ustalenia, czy aktualizacja pamięci podręcznej ustawienia czcionek i kolorów jest potrzebne przed wywołaniem metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> klasy.

### <a name="storing-and-retrieving-information"></a>Przechowywanie i pobieranie informacji o
 Uzyskać lub skonfigurować informacje, które użytkownik może modyfikować dla elementu o nazwie wyświetlanej w kategorii otwarte, wywołaj VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metody.

 Informacje o czcionki atrybutów dla konkretnej kategorii można uzyskać za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metody.

> [!NOTE]
>  `fFlags` Argumentu przekazanego do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metoda otwarcie tej kategorii definiuje zachowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody. Domyślnie te metody zwracają tylko informacje o Wyświetl elementy, które zostały zmienione. Jednak po otwarciu kategorii przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> Flaga zarówno zaktualizowane i wyświetlania niezmienione elementy są dostępne przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

 Domyślnie tylko zmienione **wyświetlania elementów** informacje są przechowywane w rejestrze. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Interfejsu nie będzie można pobrać wszystkie ustawienia czcionek i kolorów.

> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody zwracają REGDB_E_KEYMISSING, (0x80040152L) można użyć do pobrania informacji o zmianie **wyświetlania elementów**.

 Wszystkie ustawienia **wyświetlania elementów** w szczególności **kategorii** można uzyskać za pomocą metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfejsu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Implementowanie niestandardowych kategorii i wyświetlania elementów](../extensibility/implementing-custom-categories-and-display-items.md)