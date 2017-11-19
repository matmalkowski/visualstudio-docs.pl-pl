---
title: "Wybierz elementy paska narzędzi, składniki WPF | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8aaa76694a60aad5c8bfcc2dd6d26feac03ab6e1
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="choose-toolbox-items-wpf-components"></a>Wybierz elementy paska narzędzi, składniki WPF
Ta karta **wybierz elementy przybornika** okno dialogowe wyświetla listę dostępnych opcji Windows Presentation Foundation (WPF) na komputerze lokalnym. Do wyświetlania tej listy, wybierz **wybierz elementy przybornika** z **narzędzia** menu, aby wyświetlić **wybierz elementy przybornika** okno dialogowe, a następnie wybierz jego **WPF Składniki** kartę. Aby posortować wymienione składniki, wybierz nagłówek dowolnej kolumny.  

-   Zaznaczenie pola wyboru obok składnika będzie wyświetlana ikona dla tego składnika w **przybornika**.  

    > [!TIP]
    >  Aby dodać wystąpienia formantu WPF do projektu dokument otwarty do edycji, przeciągnij jego **przybornika** ikony na powierzchnię projektu widoku. Domyślne znaczników i kodu dla składnika są wstawiane do projektu, gotowy do zmodyfikowania. Aby uzyskać więcej informacji, zobacz [przy użyciu przybornika](../../ide/using-the-toolbox.md).  

-   Po wyczyszczeniu pola wyboru obok składnika odpowiednią ikonę zostaną usunięte z **przybornika.**  

    > [!NOTE]
    >  Składniki .NET Framework zainstalowanej na komputerze pozostają dostępne, czy ikony dla nich są wyświetlane w **przybornika**.  

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
**Filtr**  
Filtruje listę formantów WPF opartych na ciąg, do którego należy podać w polu tekstowym. Wyświetlane są wszystkie dopasowania z dowolnego z czterech kolumn.  

**Wyczyść**  
Czyści ciąg filtru.  

**Przeglądaj**  
Otwiera **Otwórz** okno dialogowe, które umożliwia przejście do zestawów, które zawierają formantów WPF. Umożliwia ładowanie zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów.  

**Język**  
Pokazuje zlokalizowanego języka zestawu, którego zawiera wybrany formant WPF.  

## <a name="limitations"></a>Ograniczenia  
Dodawanie formantu niestandardowego lub <xref:System.Windows.Controls.UserControl> do przybornika ma następujące ograniczenia:  

-   Działa tylko w przypadku kontrolek niestandardowych zdefiniowanych poza bieżącego projektu.  

-   Nie poprawnie zaktualizować po zmianie konfiguracji rozwiązania z debugowania do wersji lub wersji do debugowania. Jest to spowodowane odwołania nie jest odwołaniem do projektu, ale zamiast tego jest dla zestawu na dysku. Jeśli formant jest częścią bieżącego rozwiązania w przypadku zmiany z debugowania do wydania, projektu w dalszym ciągu odwołania kontroli wersji do debugowania.  

Ponadto, jeśli metadane w czasie projektowania jest stosowana do formantu niestandardowego i metadanych Określa, że <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> ma ustawioną wartość `false`, formant nie jest wyświetlany w przyborniku.  

Formanty bezpośrednio w widoku XAML można odwoływać się przez mapowanie przestrzeni nazw i zestawu dla formantu.  

## <a name="see-also"></a>Zobacz także  
[Przybornika](../../ide/reference/toolbox.md)  
[Pierwsze kroki z użyciem WPF](../../designers/getting-started-with-wpf.md)
