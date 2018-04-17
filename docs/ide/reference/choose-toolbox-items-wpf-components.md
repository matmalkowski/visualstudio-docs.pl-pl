---
title: Wybierz elementy paska narzędzi, składniki WPF | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/21/2017
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 955d0ab74d59606e63a4772aee5de96c920544ed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="choose-toolbox-items-wpf-components"></a>Wybierz elementy paska narzędzi, składniki WPF

Ta karta **wybierz elementy przybornika** okno dialogowe wyświetla listę dostępnych opcji Windows Presentation Foundation (WPF) na komputerze lokalnym. Do wyświetlania tej listy, wybierz **wybierz elementy przybornika** z **narzędzia** menu, aby wyświetlić **wybierz elementy przybornika** okno dialogowe, a następnie wybierz jego **WPF Składniki** kartę. Aby posortować wymienione składniki, wybierz nagłówek dowolnej kolumny.

- Zaznaczenie pola wyboru obok składnika będzie wyświetlana ikona dla tego składnika w **przybornika**.

    > [!TIP]
    > Aby dodać kontrolkę WPF dokumentu projektu, który jest otwarty do edycji, przeciągnij jego **przybornika** ikony na powierzchnię projektu widoku. Domyślne znaczników i kodu dla składnika są wstawiane do projektu, gotowy do zmodyfikowania. Aby uzyskać więcej informacji, zobacz [przybornika](../../ide/reference/toolbox.md).

- Po wyczyszczeniu pola wyboru obok składnika odpowiednią ikonę zostaną usunięte z **przybornika**.

    > [!NOTE]
    > Składniki .NET Framework zainstalowanej na komputerze pozostają dostępne, czy ikony dla nich są wyświetlane w **przybornika**.

Kolumn w **składników WPF** karta zawiera następujące informacje:

Nazwa  
Wyświetla listę nazw formantów WPF, dla których wpisy znajdują się w rejestrze komputera.

Przestrzeń nazw  
Wyświetla hierarchię [interfejsu API programu .NET Framework klasy](/dotnet/api/?view=netframework-4.7) przestrzeni nazw, która definiuje strukturę składnika. Sortowanie według tej kolumny listy składników dostępnych w każdym .NET Framework zainstalowany na tym komputerze.

Nazwa zestawu  
Wyświetla nazwę zestawu .NET Framework, który zawiera przestrzeń nazw dla każdego składnika. Sortowanie według tej kolumny do tworzenia listy nazw zawarte w każdej zestawu .NET Framework zainstalowana na danym komputerze.

Katalog  
Wyświetla lokalizację zestawu .NET Framework. Domyślna lokalizacja dla wszystkich zestawów to Global Assembly Cache. Aby uzyskać więcej informacji na Global Assembly Cache, zobacz [Praca z zestawami i Global Assembly Cache](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Lista elementów UI

### <a name="filter"></a>Filtr

Filtruje listę formantów WPF opartych na ciąg, do którego należy podać w polu tekstowym. Wyświetlane są wszystkie dopasowania z dowolnego z czterech kolumn.

### <a name="clear"></a>Wyczyść

Czyści ciąg filtru.

### <a name="browse"></a>Przeglądaj

Otwiera **Otwórz** okno dialogowe, które umożliwia przejście do zestawów, które zawierają formantów WPF. Umożliwia ładowanie zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów.

### <a name="language"></a>Język

Pokazuje zlokalizowanego języka zestawu, którego zawiera wybrany formant WPF.

## <a name="limitations"></a>Ograniczenia

Dodawanie formantu niestandardowego lub <xref:System.Windows.Controls.UserControl> do przybornika ma następujące ograniczenia:

- Działa tylko w przypadku kontrolek niestandardowych zdefiniowanych poza bieżącego projektu.

- Nie poprawnie zaktualizować po zmianie konfiguracji rozwiązania z debugowania do wersji lub wersji do debugowania. Jest to spowodowane odwołania nie jest odwołaniem do projektu, ale zamiast tego jest dla zestawu na dysku. Jeśli formant jest częścią bieżącego rozwiązania w przypadku zmiany z debugowania do wydania, projektu w dalszym ciągu odwołania kontroli wersji do debugowania.

Ponadto, jeśli metadane w czasie projektowania jest stosowana do formantu niestandardowego i metadanych Określa, że <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> ma ustawioną wartość `false`, formant nie jest wyświetlany w przyborniku.

Formanty bezpośrednio w widoku XAML można odwoływać się przez mapowanie przestrzeni nazw i zestawu dla formantu.

## <a name="see-also"></a>Zobacz także

[Przybornik](../../ide/reference/toolbox.md)  
[Wprowadzenie do korzystania z platformy WPF](../../designers/getting-started-with-wpf.md)
