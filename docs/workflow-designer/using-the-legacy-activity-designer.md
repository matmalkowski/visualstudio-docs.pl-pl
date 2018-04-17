---
title: Przy użyciu narzędzia Projektant działań starszych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c69c2dfdd6fb81bcb6a544f27da0874a7dc99331
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-legacy-activity-designer"></a>Przy użyciu narzędzia Projektant działań starsza wersja
W tym temacie opisano sposób używania Projektant działań w starszej wersji projektanta przepływów pracy systemu Windows. Jeśli za pomocą starszej wersji projektanta [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Projektant działań umożliwia tworzenie własnych niestandardowych działań.

## <a name="creating-a-custom-activity"></a>Tworzenie niestandardowego działania
 Wykonaj następujące kroki, aby utworzyć niestandardowe działanie przy użyciu narzędzia Projektant działań:

1.  Na **projektu** menu, kliknij przycisk **Dodaj działanie**.

2.  Wybierz **działania** lub **działania (z separacją kodu)** szablonu.

    1.  Użyj **działania** szablonu w celu utworzenia działanie z definicją działania i kodem użytkownika w tym samym pliku kodu.

    2.  Użyj **działania (z separacją kodu)** szablonu w celu utworzenia działanie z definicją działania wyrażony jako znacznik przepływu pracy i kodem użytkownika w osobnym pliku kodu.

3.  Wpisz nazwę działania lub pozostaw nazwę domyślną, a następnie kliknij przycisk **Dodaj**.

 Można również utworzyć zestaw niestandardowych działań przez utworzenie nowego projektu typu **biblioteki działań przepływów pracy**. Aby uzyskać więcej informacji o tym typie projektu, zobacz [porady: Tworzenie biblioteki działań przepływów pracy (starsze)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Konfigurowanie działania
 Gdy Projektant działań jest aktywny, można użyć przeglądarki właściwości do skonfigurowania właściwości wymienionych w poniższej tabeli.

|Właściwość|Komentarze|
|--------------|--------------|
|**Nazwa**|Nazwa działania.|
|**Klasa podstawowa**|Klasa podstawowa pochodzi z klasy działania. Domyślna klasa podstawowa jest [to SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). W **właściwości** okna, kliknij przycisk **klasa podstawowa** wielokropka **[...]**  można wybrać innej klasy podstawowej w [Wyszukaj i wybierz typ .NET dialogowe (starsze)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Opis**|Zdefiniowane przez użytkownika opis działania.|
|**włączone**|Ustaw **True** domyślnie, aby umożliwić działanie wykonywania i sprawdzania poprawności. Ustaw **False** wyłączyć działanie wykonywania i sprawdzania poprawności. Aby informacji na temat działania wykonywania i sprawdzania poprawności, zobacz [opracowywania działań przepływu pracy](http://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Dodawanie działań podrzędnych
 Działanie projektujesz można przeciągnąć działań podrzędnych z przybornika. Następnie można skonfigurować każde działanie podrzędne w przeglądarce właściwości.

## <a name="see-also"></a>Zobacz także

- [Tworzenie działań przepływu pracy](http://go.microsoft.com/fwlink?LinkID=65024)
- [Tworzenie niestandardowych działań](http://go.microsoft.com/fwlink?LinkID=65021)
- [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)
- [Przykłady niestandardowych działań](http://go.microsoft.com/fwlink?LinkID=65022)
- [Instrukcje: Tworzenie biblioteki działań przepływów pracy (starsza wersja)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)
- [Używanie starszej wersji Projektanta przepływu pracy](../workflow-designer/using-the-legacy-workflow-designer.md)