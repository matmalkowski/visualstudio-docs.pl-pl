---
title: Udostępnione kolorów dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9093eef6166c86eb6e1ffdf602b4fb75841834d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="shared-colors-for-visual-studio"></a>Udostępniony kolorów dla programu Visual Studio
Podczas projektowania interfejsu użytkownika, który korzysta z typowymi elementami powłoki programu Visual Studio lub chcesz z elementu interfejsu, aby były spójne z podobne funkcje, umożliwia istniejących nazw tokenu w plikach definicji pakietu wybierz i przypisz kolory. Dzięki temu, że Twój interfejs użytkownika jest zgodny z ogólną środowiska Visual Studio i aktualizowane automatycznie po motywów zostały dodane lub zaktualizowane.  

W tym artykule opisano typowe elementy interfejsu użytkownika i tokenu nazwy, które używają, które można odwoływać się podczas tworzenia podobnych interfejsu użytkownika. Określone informacje na temat dostępu tokeny kolorów te można wyświetlić [usługa VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  

Upewnij się, że poprawnie używać nazw tokenu:  

-   **Użyj tokenu nazw oparte na funkcji, nie na samego kolor.** Typowe kolory udostępnione są skojarzone z konkretne elementy interfejsu i tylko są przeznaczone do użycia na takie same lub podobne funkcje. Na przykład nie używać ponownie kolor pola kombi naciśniętego dla Animacja postępu Obracająca wyłącznie z powodu chcesz kolor. Funkcje pole kombi i animacji są różne, a Jeśli kolor skojarzony z zmiany pola kombi, może nie być odpowiednie kolor dla danego elementu animacji. Spójne używanie kolor pomaga orientacja użytkowników i uniknąć pomyłek.  

-   **Użyj kolorów tła i tekstu w poprawnej kombinacji.** Kolory tła, które są przeznaczone do użycia z tekstem będzie miał kolor tekstu. Nie używaj kolorów tekstu innego niż określono co w tle. Jeśli nie ma kolor tekstu, nie używaj koloru tła dla dowolnej warstwy oczekiwaną do wyświetlania tekstu. Inne kombinacje kolory tła i tekstu może spowodować interfejs nie można go odczytać.  

-   **Użyj kolorów kontroli, które są odpowiednie dla ich lokalizacji.** W określonych stanach niektóre formanty programu Visual Studio nie mają osobne obramowania i kolory tła. Zamiast tego wybierz one te kolory z powierzchni za nimi. Upewnij się, zawsze używać tokenu nazwy, które są odpowiednie dla lokalizacji, w której są umieścić formantu.  

> [!IMPORTANT]
> Nie używaj tokenów w kategorii "Stronę startową" lub "Jabłecznik."  

## <a name="common-shared-controls"></a>Formanty standardowe udostępnionego

Użycie standardowych pasek poleceń Visual Studio z funkcji, będziesz mieć dostęp do formantów powłoki styl. Szablon re nie tych wspólnych kontrolek. Jednak jeśli jest potrzebne do tworzenia pasek poleceń niestandardowych, konieczne może być tworzyć własne kontrolki również. W takim przypadku upewnij się, że Użyj poprawne nazwy tokenu dla każdego z poniższych formantów, aby Twój interfejs użytkownika jest zgodne z pozostałą częścią programu Visual Studio.

### <a name="button-controls"></a>formanty przycisków

![Kontrolka przycisku poprawek](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla przycisków w także dokument, który chcesz zintegrować z motywów programu Visual Studio (światło, ciemny, niebieski lub kompozycję Duży kontrast systemu). | ... w przypadku przycisków, która będzie wyświetlana na tle niestandardowego, który nie jest częścią motywu programu Visual Studio. |

**Przycisku: standardowa stanu**

![Przycisk standardowy](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Przycisk standardowy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.Button` |
| Obramowanie przycisku | `CommonControls.ButtonBorder` |

**Przycisk: stan domyślny**

![Przycisk domyślny](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Przycisk domyślny

| Element | Nazwa tokenu: Category.color | 
| --- | --- | 
| Przycisk | `CommonControls.ButtonDefault` |
| Obramowanie przycisku | `CommonControls.ButtonBorderDefault` |

**Przycisk: stan wyłączenia**  

![Wyłączony przycisk](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Przycisk wyłączone  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonDisabled` |
| Obramowanie przycisku | `CommonControls.ButtonBorderDisabled` |

**Przycisk: stan aktywowanego**  

![Przycisk przy aktywowaniu](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Przycisk przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonHover` |
| Obramowanie przycisku | `CommonControls.ButtonBorderHover` |

**Przycisku: stan naciśnięcia**  

![Naciśniętego przycisku](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Naciśniętego przycisku  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonPressed` |
| Obramowanie przycisku | `CommonControls.ButtonBorderPressed` |

**Przycisku: stan fokus**  

![Przycisk ukierunkowanych](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Przycisk mającego fokus  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonFocused` |
| Obramowanie przycisku | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Formanty pól wyboru  
![Pole wyboru (poprawek)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 161_CheckboxRedline")<br />Pole wyboru (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla znajdujących się w dokumencie również formanty pól wyboru. | ... dla elementów interfejsu użytkownika, który nie jest polem wyboru. |

**Pole wyboru: domyślny stan**  

![Pole wyboru](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 162_Checkbox")<br />Pole wyboru domyślne

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackground` |
| Obramowanie | `CommonControls.CheckBoxBorder` |
| Tekst | `CommonControls.CheckBoxText` |
| Symbolu | `CommonControls.CheckBoxGlyph` |

**Pole wyboru: stanu wyłączonego**  

![Wyłączone pole wyboru](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 163_CheckboxDisabled")<br />Wyłączone pole wyboru  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.CheckBoxBorderDisabled` |
| Tekst | `CommonControls.CheckBoxTextDisabled` |
| Symbolu | `CommonControls.CheckBoxGlyphDisabled` |

**Pole wyboru: wskaźnika stanu**  

 ![Pole wyboru przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 164_CheckboxHover")<br />Pole wyboru przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundHover` |
| Obramowanie | `CommonControls.CheckBoxBorderHover` |
| Tekst | `CommonControls.CheckBoxTextHover` |
| Symbolu | `CommonControls.CheckBoxGlyphHover` |  

**Pole wyboru: naciśnięty stanu**  

![Pole wyboru naciśniętego](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 165_CheckboxPressed")<br />Pole wyboru wciśnięty  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Obramowanie | `CommonControls.CheckBoxBorderPressed` |
| Tekst | `CommonControls.CheckBoxTextPressed` |
| Symbolu | `CommonControls.CheckBoxGlyphPressed` |  

**Pole wyboru: fokus stanu**  

![Pole wyboru ukierunkowanych](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 166_CheckboxFocused")<br />Pole wyboru mającego fokus  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundFocused` |
| Obramowanie | `CommonControls.CheckBoxBorderFocused` |
| Tekst | `CommonControls.CheckBoxTextFocused` |
| Symbolu | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listy rozwijane i kombi pola
![Pole kombi dół/upuszczania (poprawek)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")<br />Pole kombi dół/upuszczania (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... listach rozwijanych i kombi pola w dokumencie również. | ... dla elementów interfejsu użytkownika, którego nie ma listy rozwijanej lub pola kombi. |  
| | ... dla paska poleceń [listach rozwijanych](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) lub [pola kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Listy rozwijane i kombi pola: domyślna stanu**  

![Domyślne listy dół/kombi](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 168_DropDownComboBox")<br />Domyślne listy dół/kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackground` |
| Obramowanie | `CommonControls.ComboBoxBorder` |
| Tekst | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Symbolu | `CommonControls.ComboBoxGlyph` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackground` |

**Listy rozwijane i kombi pola: stanu wyłączonego**  

![Wyłączone upuszczania dół/kombi](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")<br />Wyłączone upuszczania dół/kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.ComboBoxBorderDisabled` |
| Tekst | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Symbolu | `CommonControls.ComboBoxGlyphDisabled` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listy rozwijane i kombi pola: wskaźnika stanu**  

![Upuść dół/kombi przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")<br />Upuść dół/kombi przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundHover` |
| Obramowanie | `CommonControls.ComboBoxBorderHover` |
| Tekst | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Symbolu | `CommonControls.ComboBoxGlyphHover` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listy rozwijane i kombi pola: naciśnięty stanu**  

![Naciśnięto upuszczania dół/kombi](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")<br />Naciśnięto upuszczania dół/kombi  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundPressed` |
| Obramowanie | `CommonControls.ComboBoxBorderPressed` |
| Tekst | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Symbolu | `CommonControls.ComboBoxGlyphPressed` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Listy rozwijane i kombi pola listy, widok elementu: naciśnięty stanu**  

 ![Upuść dół/kombi naciśnięty widok elementu listy](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")<br />Upuść dół/kombi naciśnięty widok elementu listy  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło |  `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Tekst elementu | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Tło, cień | `CommonControls.ComboBoxListBackgroundShadow` |

**Listy rozwijane i kombi pola: fokus stanu**  

![Upuść dół/kombi z fokusem](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")<br />Pole kombi dół/upuszczania z fokus

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxBorderFocused` |
| Tekst | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Symbolu | `CommonControls.ComboBoxGlyphFocused` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listy rozwijane i kombi pola: tekst wejściowy zaznaczenia**  

![Pola kombi dół/upuszczanie tekstu wejściowych wybór](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")<br />Wybór danych wejściowych pola kombi dół/upuszczanie tekstu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Wyróżnij | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Formanty danych tabelarycznych (siatki)  
Formanty danych tabelarycznych, znanej także jako formanty siatki, są formanty standardowe dla programu Visual Studio, który może służyć do prezentowania dużych ilości danych w wielu kolumnach. Formanty standardowe dane tabelaryczne znajdują się w wielu miejscach w programie Visual Studio: w oknie Lista błędów narzędzia, raporty IntelliTrace i widok sterty w pamięci, między innymi. Należy zawsze używać formantów standardowych danych tabelarycznych podane. W sporadycznych przypadkach możesz utracić dostęp do formantów standardowych danych tabelarycznych. W takich sytuacjach należy stosować następujących nazw tokenu do upewnij się, że Twój interfejs użytkownika jest zgodny z innych formantów danych tabelarycznych w programie Visual Studio.  

![Formant siatki/danych tabelarycznych (poprawek)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")<br />Formant siatki/danych tabelarycznych (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla tabelarycznym lub kontrolki siatki. | ... dla elementów interfejsu użytkownika, który nie jest tabelarycznym lub kontrolce siatki. |

#### <a name="column-headers"></a>Nagłówki kolumn  
Nagłówki kolumn składają się z tło, obramowanie tekstu tytułu i opcjonalnie symbolu zazwyczaj używany, gdy siatki jest sortowana według tej kolumny.  

**Nagłówek kolumny: domyślna stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Header.Default` |
| Narzędzia (tekst) | `Environment.CommandBarTextActive` |
| Narzędzia (symbol) | `Header.Glyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: wskaźnika stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Header.MouseOver` |
| Narzędzia (tekst) | `Environment.CommandBarTextHover` |
| Narzędzia (symbol) | `Header.MouseOverGlyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: naciśnięty stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Narzędzia (tekst) | `CommonControls.CheckBoxBorderPressed` |
| Narzędzia (symbol) | `CommonControls.CheckBoxTextPressed` |
| Obramowanie | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Elementy widoku listy  
 Tło i zawartości składają się elementy widoku listy. Zawartość może być tekstu i/lub ikony.  

**Elementy widoku listy: domyślna stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Przezroczyste |
| Narzędzia (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Brak |

**Elementy widoku listy: stan aktywny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Narzędzia (tekst) | `TreeView.SelectedItemActiveText` |
| Obramowanie | Brak |

**Elementy widoku listy: stan nieaktywny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Narzędzia (tekst) | `TreeView.SelectedItemInactiveText` |
| Obramowanie | Brak |  

### <a name="ui-text"></a>Tekst interfejsu użytkownika

#### <a name="instructional-text"></a>Tekst informacyjny
Tekst informacyjny udostępnia wyraźne wyjaśnienie głównym co można zrobić w oknie dialogowym lub dokumentu na stronie.

![Domyślny tekst informacyjny](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Domyślny tekst informacyjny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Tekst informacyjny dodatkowej
Na stronach dokumentu z dużą ilością tekstu i formantów niektóre tekst informacyjny używa wartości kolorów. Dzięki temu mogą służyć do przekazywania informacji, które jest najbardziej ważne i zmniejszenia gęstość elementy interfejsu użytkownika. (Zobacz też poniżej sekcję tekstu podpowiedzi.)

![Tekst informacyjny dodatkowej](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Tekst informacyjny dodatkowej

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Tekst wskazówki
Wskazówka tekst wyświetlany w pusty kontroli poniżej lub na powierzchni pustego dokumentu do wyświetlenia użytkownika, co zrobić dalej. Tekst wskazówki można użyć z okna lub formant tła.

**Domyślny tekst wskazówki**

![Domyślny tekst podpowiedzi](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Domyślny tekst wskazówki

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.ControlEditHintText` |

**Tekst podpowiedzi wymagane**

![Wymagany tekst podpowiedzi](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Tekst podpowiedzi wymagane

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.ControlRequiredHintText` |
| Tło | `Environment.ControlRequiredBackground` |

**Tekst formantu pole wyszukiwania**

> Zobacz [pola wyszukiwania](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) innych tokenów kolor powiązane ze sterowaniem wyszukiwania.

![Wyszukaj tekst formantu pole](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Tekst formantu pole wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink  
Hiperłącze jest jeden formant, który nie zawiera pary narzędzia/tła. We wszystkich przypadkach Użyj hyperlink kolor pierwszego planu, który pojawi się prawidłowo na ciemny, szary i białe tło. Jeśli token kolor nie jest używany dla formantu hiperłącza, zobaczysz domyślnego systemu koloru "naciśnięty", który czerwono. To sygnał, że kontrolka nie jest za pomocą tokenu kolor poprawne środowisko.  

![HYPERLINK (poprawek)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 133_HyperlinkRedline")<br />HYPERLINK (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... Aby utworzyć niestandardowe hiperłącze. | ... dla wszystkich elementów, które nie jest hiperłącze. |

**Hiperłącze: stan domyślny**  

![Domyślne hiperłącze](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 134_Hyperlink")<br />Domyślne hiperłącze

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.PanelHyperlink` |

**Hiperłącze: stan aktywowanego**

![HYPERLINK przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 135_HyperlinkHover")<br />HYPERLINK przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.PanelHyperlinkHover` |

**Hiperłącze: stan naciśnięcia**

![Hyperlink naciśniętego](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 136_HyperlinkPressed")<br />Hyperlink wciśnięty  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.PanelHyperlinkPressed` |

**Hiperłącza: stan wyłączonego**

![Wyłączonego hiperłącza](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 137_HyperlinkDisabled")<br />Wyłączonego hiperłącza  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars  
Infobars są używane do zawierają więcej informacji o danym kontekście i zawsze są wyświetlane w górnej części okna dokumentu lub okna narzędzia.  

![Pasek informacyjny (poprawek)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 138_InfobarRedline")<br />Pasek informacyjny (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia niestandardowego infobars. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego. |

**Informacyjnym: stan domyślny**

![Domyślna informacyjnym](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 139_Infobar")<br />Domyślne informacyjny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.InfoBarBackground` |
| Narzędzia (tekst) | `InfoBar.InfoBar` |
| Obramowanie | `InfoBar.InfoBarBorder` |

**Zamknij pasek informacyjny (&times;) przycisk: domyślna stanu**

![Domyślna Zamknij informacyjny (&times;) przycisk](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Domyślna Zamknij informacyjny (&times;) przycisku

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButton` |
| Obramowanie | `InfoBar.CloseButtonBorder` |
| Symbolu | `InfoBar.CloseButtonGlyph` |

**Zamknij pasek informacyjny (&times;) przycisk: wskaźnika stanu**

![Zamknij pasek informacyjny (&times;) przycisk przy aktywowaniu](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Zamknij pasek informacyjny (&times;) przycisk przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButtonHover` |
| Obramowanie | `InfoBar.CloseButtonHoverBorder` |
| Symbolu | `InfoBar.CloseButtonHoverGlyph` |

**Zamknij pasek informacyjny (&times;) przycisk: naciśnięty stanu**

![Naciśnięto Zamknij informacyjny (&times;) przycisk](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Naciśnięto Zamknij informacyjny (&times;) przycisku

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButtonDown` |
| Obramowanie | `InfoBar.CloseButtonDownBorder` |
| Symbolu | `InfoBar.CloseButtonDownGlyph` |

**Przycisk hiperłącza informacyjnym: domyślna stanu**

![Domyślny przycisk hiperłącze informacyjnym](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Przycisk hiperłącze informacyjnym domyślny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `InfoBar.Hyperlink` |

**Przycisk hiperłącza informacyjnym: wskaźnika stanu**

![Przycisk hiperłącza informacyjnym przy aktywowaniu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Przycisk hiperłącza informacyjnym przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreślenie) |

**Przycisk hiperłącza informacyjnym: naciśnięty stanu**

![Informacyjnym naciśniętego przycisku hyperlink](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Informacyjnym naciśniętego przycisku hiperłącza

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreślenie) |

**Hyperlink wbudowany pasek informacyjny (w ramach zdania): domyślna stanu**

![Domyślny wbudowany pasek informacyjny hyperlink przycisk](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Przycisk hiperłącza informacyjnym wbudowanego domyślnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `InfoBar.Hyperlink` |

**Hyperlink wbudowany pasek informacyjny (w ramach zdania): wskaźnika stanu**

![Przycisk hiperłącza wbudowany pasek informacyjny przy aktywowaniu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Przycisk hiperłącza wbudowany pasek informacyjny przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreślenie) |

**Hyperlink wbudowany pasek informacyjny (w ramach zdania): naciśnięty stanu**

![Przycisk hiperłącza wbudowany pasek informacyjny naciśniętego](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Naciśnięty przycisk hiperłącza wbudowany pasek informacyjny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreślenie) |

**Przycisk paska informacyjnego: domyślna stanu**

![Przycisk domyślny informacyjnym](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Przycisk domyślny informacyjny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.Button` |
| Narzędzia (tekst) | `InfoBar.Button` |
| Obramowanie | `InfoBar.ButtonBorder` |

**Przycisk paska informacyjnego: wskaźnika stanu**

![Przycisk paska informacyjnego przy aktywowaniu](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Przycisk paska informacyjnego przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseOver` |
| Narzędzia (tekst) | `InfoBar.ButtonMouseOver` |
| Obramowanie | `InfoBar.ButtonMouseOverBorder` |

**Przycisk paska informacyjnego: naciśnięty stanu**

![Informacyjnym naciśniętego przycisku](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Informacyjnym naciśniętego przycisku

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseDown` |
| Narzędzia (tekst) | `InfoBar.ButtonMouseDown` |
| Obramowanie | `InfoBar.ButtonMouseDownBorder` |

**Przycisk paska informacyjnego: stanu wyłączonego**

![Przycisk wyłączonego paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Przycisk wyłączonego paska informacyjnego.

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonDisabled` |
| Narzędzia (tekst) | `InfoBar.ButtonDisabled` |
| Obramowanie | `InfoBar.ButtonDisabledBorder` |

**Przycisk paska informacyjnego: fokus stanu**

![Przycisk paska informacyjnego ukierunkowanych](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Przycisk ukierunkowanych informacyjny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonFocus` |
| Narzędzia (tekst) | `InfoBar.ButtonFocus` |
| Obramowanie | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Paski przewijania  
Paski przewijania są wstawiony przez środowisko Visual Studio i nie można utworzyć motywu. Jednak można zdecydować, że chcesz wykorzystać kolory używane w paski przewijania, tak aby Twój interfejs użytkownika zawsze wyświetlany jest zgodne z tej części środowiska Visual Studio.  

![Pasek przewijania (poprawek)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 140_ScrollbarRedline")<br />Pasek przewijania (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... przy tworzeniu interfejsu użytkownika który chcesz dopasować paski przewijania programu Visual Studio. | ... dla wszystkich elementów, nie chcesz, aby zawsze odpowiadać interfejsu użytkownika — paska przewijania. |

**Pasek przewijania: domyślna stanu**  

![Pasek przewijania domyślne](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 141_Scrollbar")<br />Domyślny pasek przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Narzędzia (przenośny) | `Environment.ScrollBarThumbBackground` |

**Pasek przewijania: wskaźnika stanu**

![Pasek przewijania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 143_ScrollbarHover")<br />Pasek przewijania przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Narzędzia (przenośny) | `Environment.ScrollBarThumbMouseOverBackground` |

*Pasek przewijania: naciśnięty stanu**

![Pasek przewijania naciśniętego](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 145_ScrollbarPressed")<br />Naciśnięto paska przewijania  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Narzędzia (przenośny) | `Environment.ScrollBarThumbPressedBackground` |

**Paska strzałkę przewijania: domyślna stanu**  

![Strzałkę paska przewijania domyślne](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 142_ScrollbarArrow")<br />Strzałkę paska przewijania domyślne

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowBackground`<br />(Ustaw kolor paska przewijania). |
| Narzędzia (symbol) | `Environment.ScrollBarArrowGlyph` |

**Paska strzałkę przewijania: wskaźnika stanu**

![Paska strzałkę po aktywowaniu przewijania](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br />Strzałka paska przewijania przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowMouseOverBackground`<br />(Ustaw kolor paska przewijania). |
| Narzędzia (symbol) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Paska strzałkę przewijania: naciśnięty stanu**  

![Strzałka paska przewijania naciśniętego](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br />Naciśnięty klawisz strzałki paska przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowPressedBackground`<br />(Ustaw kolor paska przewijania). |
| Narzędzia (symbol) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Pola wyszukiwania  
Jeśli to możliwe, użyj wspólnego formantu wyszukiwania udostępniane przez środowisko Visual Studio. Kolory — okno wyszukiwania znajdują się w kategorii "SearchControl" w **ShellColors.pkgdef** pliku, który zawiera token nazwy pola wejściowego, przycisku akcji, przycisku rozwijanego i menu rozwijanego.  

Pole wyszukiwania może być jednym z kilku stanów, niektóre z nich wzajemnie się wykluczają:  

-   "Fokus" lub "bez fokusu" odwołuje się do czy kursor znajduje się w polu tekstowym.  

-   "Active" lub "nieaktywne" odwołuje się do tego, czy użytkownik ma wejściowych zapytania wyszukiwania w polu tekstowym.  

-   "Hover" oznacza, że użytkownik ma moused w polu wyszukiwania przy użyciu myszy (ten stan zastępuje wszystkie inne stany).  

-   "Wyłączone" oznacza, że funkcja wyszukiwania jest wyłączona dla bieżącego kontekstu.  

![Pole wyszukiwania (poprawek)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 110_SearchBoxRedline")<br />Pole wyszukiwania (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas projektowania pole wyszukiwania niestandardowego. | ... dla wszystkich elementów, które nie jest pole wyszukiwania. |
| | ... dla wszystkich elementów, których nie chcesz, aby zawsze odpowiadać wyszukiwania pola interfejsu użytkownika. |

**Fokus wprowadzania pola wyszukiwania**

![Pole wejściowe wyszukiwania ukierunkowanych](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br />Fokus wprowadzania pola wyszukiwania  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.FocusedBackground` |
| Narzędzia (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Pole wejściowe wyszukiwania bez fokusu, aktywny**

![Pole wejściowe wyszukiwania bez fokusu](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br />Pole wejściowe wyszukiwania bez fokusu, aktywny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.SearchActiveBackground` |
| Narzędzia (tekst) | `SearchControl.SearchActiveBackground` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Pole wejściowe bez fokusu, nieaktywne wyszukiwania**

![Pole wejściowe wyszukiwania bez fokusu, nieaktywne](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Pole wejściowe bez fokusu, nieaktywne wyszukiwania  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Unfocused` |
| Narzędzia (tekst) | `SearchControl.Unfocused` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Pole wejściowe wyróżnione wyszukiwania (tylko tekst)**

![Pole wejściowe wyszukiwania wyróżnione](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br />Pole wejściowe wyróżnione wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Selection` |
| Narzędzia (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | Brak |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Wyłączone pole wejściowe wyszukiwania**

![Wyłączone pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br />Wyłączone pole wejściowe wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Disabled` |
| Narzędzia (tekst) | `SearchControl.Disabled` |
| Obramowanie | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Przycisk akcji ukierunkowanych wyszukiwania**

![Fokus przycisku akcji wyszukiwania](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br />Przycisk akcji ukierunkowanych wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (wyszukiwania symboli) | `SearchControl.SearchGlyph` |
| Narzędzia (Zatrzymaj symboli) | `SearchControl.StopGlyph` |
| Narzędzia (Wyczyść symboli) | `SearchControl.ClearGlyph` |
| Obramowanie | Brak |

**Przycisk akcji wyszukiwania bez fokusu**  

![Przycisk akcji bez fokusu wyszukiwania](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br />Przycisk akcji wyszukiwania bez fokusu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (wyszukiwania symboli) | `SearchControl.SearchGlyph` |
| Narzędzia (Zatrzymaj symboli) | `SearchControl.StopGlyph` |
| Narzędzia (Wyczyść symboli) | `SearchControl.ClearGlyph` |
| Obramowanie | Brak |

**Naciśnięciu przycisku akcji wyszukiwania**

![Wyszukiwanie naciśniętego przycisku akcji](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Naciśnięciu przycisku akcji wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.ActionButtonMouseDown` |
| Narzędzia (symbol) | `SearchControl.ActionButtonMouseDownGlyph` |
| Obramowanie | `SearchControl.ActionButtonMouseDownBorder` |

**Przycisk akcji wyszukiwania wyłączone**

![Przycisk akcji wyszukiwania wyłączone](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br />Przycisk akcji wyszukiwania wyłączone

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (symbol) | `SearchControl.ActionButtonDisabledGlyph` |
| Obramowanie | Brak |

**Przycisk rozwijany ukierunkowanych wyszukiwania**

![Przycisk rozwijany ukierunkowanych wyszukiwania](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br />Przycisk rozwijany ukierunkowanych wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.FocusedDropDownButton` |
| Narzędzia (symbol) | `SearchControl.FocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.FocusedDropDownButtonBorder` |

**Przycisk rozwijany wyszukiwania bez fokusu**

![Przycisk rozwijany bez fokusu wyszukiwania](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br />Przycisk rozwijany wyszukiwania bez fokusu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.UnfocusedDropDownButton` |
| Narzędzia (symbol) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.UnfocusedDropDownButtonBorder` |

**Naciśnięciu przycisku rozwijanego wyszukiwania**

![Wyszukiwanie naciśniętego przycisku rozwijanego](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Naciśnięciu przycisku rozwijanego wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.MouseDownDropDownButton` |
| Narzędzia (symbol) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Obramowanie | `SearchControl.MouseDownDropDownButtonBorder` |

**Przycisk rozwijany wyszukiwania wyłączone**

![Przycisk rozwijany wyszukiwanie wyłączone](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br />Przycisk rozwijany wyszukiwania wyłączone

| Element | Nazwa tokenu: Category.color |
| --- | --- |  
| Tło | Brak |
| Narzędzia (symbol) | `SearchControl.DisabledDownButtonGlyph` |
| Obramowanie | Brak |

#### <a name="search-drop-down-lists"></a>Listy rozwijane wyszukiwania  
Menu rozwijane pole wyszukiwania może być nieco bardziej skomplikowane niż inne menu rozwijane w programie Visual Studio. "Wyszukiwanie sugerowane" i sekcje "Opcje wyszukiwania" może występować samodzielnie lub w menu i każdej z nich jest pokolorowane oddzielnie. Wiersz również oddziela te dwie sekcje, gdy pojawią się ze sobą i obramowanie wokół menu rozwijane całego.  

![Listy rozwijanej wyszukiwania (poprawek)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 124_SearchDropdownRedline")<br />Listy rozwijanej wyszukiwania (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia listy rozwijanej wyszukiwania niestandardowego. | ... dla listy rozwijanej, które są widoczne w innych kontekstach. |
| ... poprawne nazwy tokenu dla składników poprawnej listy. | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Elementy listy rozwijanej wyszukiwania**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Obramowanie | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| Cień | `Environment.DropShadowBackground` |

**Sugerowana wyszukiwania: domyślna stanu**

![Domyślne sugerowane wyszukiwania](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 125_SearchSuggested")<br />Domyślne sugerowane wyszukiwania  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `SearchControl.PopupItemText` |

**Sugerowana wyszukiwania: wskaźnika stanu**

![Sugerowana wyszukiwania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br />Sugerowane wyszukiwania przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `SearchControl.PopupMouseOverItemText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: domyślna stanu**

![Pole wyboru wyszukiwania](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 126_SearchCheckbox")<br />Domyślne opcje wyszukiwania (pole wyboru)  

![Opcje wyszukiwania](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 127_SearchOptions")<br />Domyślne opcje wyszukiwania (łącze)  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (pole tekstowe) | `SearchControl.PopupCheckboxText` |
| Narzędzia (tekst łącza) | `SearchControl.PopupButtonText` |
| Tło nagłówka | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst nagłówka) | `SearchControl.PopupSectionHeaderText` |

**Opcje wyszukiwania: wskaźnika stanu**

![Opcje (pole wyboru) wyszukiwania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br />Opcje wyszukiwania (pole wyboru) przy aktywowaniu  

![Opcje (łącze) wyszukiwania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 130_SearchOptionsHover")<br />Opcje wyszukiwania (łącze) przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (pole tekstowe) | `SearchControl.PopupCheckboxMouseDownText` |
| Narzędzia (tekst łącza) | `SearchControl.PopupButtonMouseDownText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: naciśnięty stanu**  

![Naciśnięto opcje wyszukiwania (pole wyboru)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br />Naciśnięto opcje wyszukiwania (pole wyboru)   

![Naciśnięto opcje wyszukiwania (łącze)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 132_SearchOptionsPressed")<br />Naciśnięto opcje wyszukiwania (łącze)  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło pola wyboru | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (pole tekstowe) | `SearchControl.PopupCheckboxMouseDownText` |
| Łącze tła | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst łącza) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a> Widok drzewa  
Hierarchiczna schematu organizacyjnego którego kolory są kontrolowane przez nazwy kolorów w zaimplementować kilka okien narzędzi, w tym Eksploratorze rozwiązań, Eksploratora serwera i widoku klas `TreeView` kategorii. Wszystkie elementy w widoku drzewa ma kolory tła i tekstu. Elementy, które mają zagnieżdżone elementy podrzędne również mają symboli, które wskazują, czy element jest rozwinięte lub zwinięte.  

![Widok drzewa (poprawek)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 147_TreeViewRedline")<br />Widok drzewa (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym należy zaimplementować hierarchiczny widok organizacji. | ... dla wszystkich elementów, które nie jest podobny do widoku drzewa. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Element widoku drzewa: domyślna stanu**

![Element widoku drzewa domyślny](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 148_TreeView")<br />Element widoku drzewa domyślny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.Background` |
| Narzędzia (tekst) | `TreeView.Background` |
| Narzędzia (symbol) | `TreeView.Glyph` |
| Obramowanie | Brak |

**Element widoku drzewa: wskaźnika stanu**

![Element widoku drzewa przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 149_TreeViewHover")<br />Element widoku drzewa przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.Background` |  
| Narzędzia (tekst) | `TreeView.Background` |
| Narzędzia (symbol) | `TreeView.GlyphMouseOver` |
| Obramowanie | Brak |

**Element widoku drzewa: przeciągnij stanu**

![Drzewa elementu widoku na przeciągania za pośrednictwem](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 150_TreeViewDragOver")<br />Przeciągnij element widoku drzewa na  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.DragOverItem` |
| Narzędzia (tekst) | `TreeView.DragOverItem` |
| Narzędzia (symbol) | `TreeView.DragOverItemGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: zaznaczone, fokus stanu**

![Wybrane i fokus elementu widoku drzewa](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 151_TreeViewFocused")<br />Element widoku drzewa wybranych i skupiają się

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Narzędzia (tekst) | `TreeView.SelectedItemActive` |
| Narzędzia (symbol) | `TreeView.SelectedItemActiveGlyph` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: stan wybranego, bez fokusu**  

![Element widoku drzewa wybrane i bez fokusu](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 152_TreeViewUnfocused")<br />Element widoku drzewa wybrane i bez fokusu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Narzędzia (tekst) | `TreeView.SelectedItemInactive` |
| Narzędzia (symbol) | `TreeView.SelectedItemInactiveGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: aktywowany, zaznaczone, a fokus stanu**

![Wybrane i fokus elementu widoku drzewa przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br />Element widoku drzewa wybranych i skupiają się na aktywowany  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Narzędzia (tekst) | `TreeView.SelectedItemActive` |
| Narzędzia (symbol) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: stan aktywowany, wybranych i bez fokusu**

![Element widoku drzewa wybrane i bez fokusu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br />Element widoku drzewa wybrane i bez fokusu przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Narzędzia (tekst) | `TreeView.SelectedItemInactive` |
| Narzędzia (symbol) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | Brak |

## <a name="shell-appearance"></a>Wygląd powłoki

### <a name="background"></a>Tło  
Tło środowiska składa się z dwóch warstw. Dolna warstwa jest pełny kolor, który obejmuje całą IDE. Górną warstwę mieści się w obszarze półki polecenia i między kanałami automatyczne ukrywanie okna narzędzia na lewej i prawej krawędzi IDE. Warstwy tła górny i dolny są ustawione na ten sam kolor w jasny i ciemny motywów.  

![Visual Studio shell tła (poprawek)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 187_ShellBackgroundRedline")<br />Visual Studio shell tła (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla miejsca, w którym chcesz dopasować tło środowiska Visual Studio. | ... jako wypełnienia dla miejsca, które nie są tła powierzchni. |
| | ... jako tło do umieszczenia na elementy pierwszego planu. |

**Dolnej warstwy powłoki wyglądu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |  
| Tło | `Environment.EnvironmentBackground` |

**Górną warstwę powłoki wyglądu**

> Zestaw do tej samej wartości kolorów w Visual Studio 2013 jasny i ciemny motywów zatrzymania gradientu.

| Element | Nazwa tokenu: Category.color |
| --- | --- |  
| Tło | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |  

### <a name="command-shelf"></a>Polecenie półki  
Dwa zestawy tokenu nazw są używane dla tła półki polecenia: on ustawiony, dla których znajduje się na pasku menu i jeden dla których sit pasków poleceń. Grupa pasek indywidualne polecenie ma własne wartości kolorów tła, co omówiono bardziej szczegółowo w sekcji "pasek poleceń". Pasek i polecenia menu Tekst paska została szczegółowo opisana w sekcji paska menu i poleceń odpowiednio.  

![Visual Studio polecenia półki (poprawek)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 188_CommandShelfRedline")<br />Visual Studio polecenia półki (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla obszarów, gdzie umieścić menu i pasków narzędzi. | ... dla obszarów, które nie są podobne do półki polecenia. |
|... with kombinacja nazwa tokenu poprawne tła/pierwszego planu. | |

**Pasek menu polecenie półki**

> Zestaw do tej samej wartości kolorów w Visual Studio 2013 jasny i ciemny motywów zatrzymania gradientu.

| Element | Nazwa tokenu: Category.color |
| --- | --- |  
| Tło | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

** Polecenie półki polecenia pasek **

> Zestaw do tej samej wartości kolorów w Visual Studio 2013 jasny i ciemny motywów zatrzymania gradientu.

| Element | Nazwa tokenu: Category.color |
| --- | --- |  
| Tło | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest Designer  
Projektant manifestu zaprojektowano tak, aby ułatwić edytowanie pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Gdy nie jest dostępny do użycia przez ma udostępniony framework, może być odpowiednie dla Ciebie odpowiadające układ i kolory karty orientacji/nawigacji i ogólną strukturę. Aby uzyskać więcej informacji o układzie szczegóły, zobacz [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  

![Projektant manifestu (poprawek)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 175_ManifestDesignerRedline")<br />Projektant manifestu (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla projektantów, które są podobne do projektanta manifestu. | ... Jeśli masz więcej niż sześciu karty. |
| ... zamiast używanie formantów wspólnych kartę w górnej części edytora w dokumencie prawidłowo. | ... dla elementów interfejsu użytkownika, który nie jest strukturalnych, takich jak projektanta manifestu. |

**Wybrana karta manifestu projektanta: domyślna stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.TabActive` |
| Obramowanie | Brak |

**Manifestu okienko opisu wybranego projektanta: domyślna stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.DescriptionPane` |

**Manifest Designer wybranej strony zawartości: domyślna stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Background` |
| Tekst pomocy w oknie dialogowym | `ManifestDesigner.WatermarkText`<br />(Jest to nazwa tokenu niezgodny jej funkcji). |

**Karta projektanta manifestu: niezaznaczoną stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Inactive` |

**Karta projektanta manifestu: wskaźnika stanu**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Polecenie struktury  

###  <a name="BKMK_CommandMenus"></a> Menu  
Menu może wystąpić w kilku miejscach w programie Visual Studio: na pasku menu głównego, osadzonych dokumentu lub narzędzia systemu windows lub kliknij prawym przyciskiem myszy w różnych miejscach w środowisku IDE. W sekcji odpowiedniego elementu omówiono implementacje menu skojarzone z inne elementy interfejsu użytkownika. Zawsze należy używać implementacji standardowe menu udostępniane przez środowisko Visual Studio. Jednak w sporadycznych przypadkach możesz utracić dostęp do standardowe menu programu Visual Studio. W takich sytuacjach należy stosować następujących nazw tokenu do upewnij się, że Twój interfejs użytkownika jest zgodny z innych menu w programie Visual Studio.  

![Visual Studio menu (poprawek)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 000_MenuRedline")<br />Visual Studio menu (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... Jeśli musisz utworzyć niestandardowe menu.| ... tylko kolor tła. Określone zawsze używać kombinacji tła/pierwszego planu. |
| ... Jeśli masz nowy składnik interfejsu użytkownika, który chcesz dopasować menu programu Visual Studio.| |

#### <a name="menu-titles"></a>Tytuły menu  
Tytuły menu składają się z tło, obramowanie i tekst tytułu, a także opcjonalnie symbolu zwykle, gdy menu znajduje się na pasku poleceń.  

![Tytuł menu (poprawek)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 001_MenuTitleRedline")<br />Tytuł menu (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... zawsze, gdy tworzysz tytuł menu niestandardowe. | ... dla wszystkich elementów, które nie chcesz, aby zawsze odpowiada tytuł menu. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Tytuł menu: domyślna stanu**

![Domyślny tytuł menu](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 002_MenuTitleDefault")<br />Domyślny tytuł menu

![Domyślny tytuł menu z symbolem](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br />Domyślny tytuł menu z symbolami

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (tekst) | `Environment.CommandBarTextActive` |
| Narzędzia (symbol) | `Environment.CommandBarMenuGlyph` |
| Obramowanie | Brak |

**Tytuł menu: wskaźnika stanu**  

![Tytuł menu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 004_MenuTitleHover")<br />Tytuł menu przy aktywowaniu  

![Tytuł menu z symbolem przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br />Tytuł menu z symbolem przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.CommandBarTextHover` |
| Narzędzia (symbol) | `Environment.CommandBarMenuMouseOverGlyph` |  
| Obramowanie | `Environment.CommandBarBorder` |

**Tytuł menu: naciśnięty stanu**  

![Naciśnięto tytuł menu](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 006_MenuTitlePressed")<br />Tytuł naciśniętego menu

![Naciśnięto tytuł menu z symbolem](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br />Naciśnięto tytuł menu z symbolami

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.CommandBarTextActive` |
| Narzędzia (symbol) | `Environment.CommandBarMenuMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder`<br />(Tylko po lewej górnej i prawej strony.) |  

**Tytuł menu: wyłączono stanu**  

![Wyłączone tytuł menu z symbolem](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br />Tytuł menu wyłączone z symbolami

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (tekst) | `Environment.CommandBarTextInactive` |
| Narzędzia (symbol) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |

#### <a name="menu-items"></a>Elementy menu
Element menu poszczególnych składa się z tekstu menu i opcjonalnej ikony, pole wyboru lub symbolu podmenu. Jego tekstu i tła zmiana koloru przy aktywowaniu. Ten token kolor jest parę tła/pierwszego planu.  

![Elementy menu poprawek](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")  

| Użyj... | Nie używaj...  |
|---|---|
| ... dla żadnej listy rozwijanej który jest uruchamiany z paska menu lub pasek poleceń. | ... dla żadnej listy rozwijanej w innym kontekście. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Elementy menu: domyślna stanu**

![Domyślne elementy menu](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 010_MenuDefault")<br />Domyślne elementy menu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.CommandBarTextActive` |
| Narzędzia (podmenu symboli) | `Environment.CommandBarMenuSubmenuGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder` |
| Tło ikony kanału | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| Cień | `Environment.DropShadowBackground` |

**Elementy menu: zaznaczony i wybrany stanów**  

![Menu zaznaczone](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 011_MenuChecked")<br />Element menu zaznaczenia

![Po zaznaczeniu menu](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 012_MenuSelected")<br />Wybrany element menu    

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Znacznik wyboru | `Environment.CommandBarCheckBox` |  
| Znacznik wyboru tła | `Environment.CommandBarSelectedIcon` |  
| Tło ikony | `Environment.CommandBarSelected` |
| Ikona obramowania | `Environment.CommandBarSelectedBorder` |

**Elementy menu: wskaźnika stanu**  

![Umieść menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 013_MenuHover")<br />Element menu przy aktywowaniu

![Aktywowany menu zaznaczone](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 014_MenuHoverChecked")<br />Zaznaczone elementu menu przy aktywowaniu

![Aktywowany menu wybrane](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 015_MenuHoverSelected")<br />Wybrany element menu przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuItemMouseOver` |
| Narzędzia (tekst) | `Environment.CommandBarMenuItemMouseOver` |
| Narzędzia (podmenu symboli) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Znacznik wyboru | `Environment.CommandBarCheckBoxMouseOver` |
| Znacznik wyboru tła | `Environment.CommandBarHoverOverSelectedIcon` |
| Tło ikony | `Environment.CommandBarHoverOverSelected` |
| Ikona obramowania | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Elementy menu: wyłączono stanu**  

![Menu wyłączone](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 016_MenuDisabled")<br />Wyłączonego elementu menu

![Zaznaczone wyłączone menu](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 017_MenuDisabledChecked")<br />Wyłączonego elementu menu znacznika wyboru

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Narzędzia (tekst) | `Environment.CommandBarTextInactive` |
| Narzędzia (podmenu symboli) | `Environment.CommandBarMenuSubmenuGlyph` |
| Znacznik wyboru | `Environment.CommandBarCheckBoxDisabled` |
| Znacznik wyboru tła | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Paski poleceń  
Pasek poleceń może występować w wielu miejscach w programie Visual Studio IDE głównie półki polecenia i narzędzia osadzone w lub okna dokumentów.  

Ogólnie rzecz biorąc należy zawsze używać implementacja paska poleceń standardowych, które są udostępniane przez środowisko Visual Studio. Za pomocą standardowego mechanizmu zapewnia są prawidłowo wyświetlane wszystkie szczegóły visual i że elementy interakcyjne będą zachowywać się spójne z inne formanty paska poleceń Visual Studio. Jednak jeśli jest to niezbędne do tworzenia własnych pasek poleceń, upewnij się, że poprawnie za pomocą następujących nazw tokenu stylu.  

![Pasek poleceń poprawek](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 018_CommandBarRedline")<br />Pasek poleceń (poprawek)  

![Poprawek w przycisku przeciążenia](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 019_OverflowButtonRedline")<br />Przycisk przepełnienie (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... w miejscach wymagających pasek poleceń osadzone, ale są nie można użyć standardowa implementacja paska poleceń Visual Studio. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla innych niż te, dla których określono nazwy tokenu składniki paska poleceń. |

#### <a name="command-bar-groups"></a>Grupy pasek poleceń  
Grupy pasek poleceń składa się z zestawu pokrewnych formanty paska poleceń i może zawierać dowolną liczbę przycisków podziału przycisków, menu rozwijane, pola kombi lub menu. Kolory tych kontrolek obowiązują Rozdziel nazwy tokenu i są indywidualnie w innym miejscu omówione w tym przewodniku. Linii separatora służy do dzielenia grupy pasek poleceń na podgrupy powiązane.  

![Grupa pasek poleceń poprawek](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 020_CommandBarGroupRedline")<br />Grupa pasek poleceń (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |  
| ... w miejscach wymagających pasek poleceń osadzone, ale są nie można użyć standardowa implementacja paska poleceń Visual Studio. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla innych niż te, dla których określono nazwy tokenu składniki paska poleceń. |

**Grupa pasek poleceń: domyślna stanu**  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Obramowanie | `Environment.CommandBarToolBarBorder` |
| Przeciągnij uchwyt | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ikony poleceń  
![Ikona polecenia poprawek](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 021_CommandIconRedline1")<br />Ikona polecenia (poprawek)  

![Ikona polecenia tekstem poprawek](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 022_CommandIconRedline2")<br />Ikona polecenia tekstem (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla przycisków, która zostanie umieszczona na pasku poleceń. | ... dla formantów, które mają własne nazwy tokenu. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Ikona polecenia: domyślna stanu**  

![Polecenie domyślna ikona](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 023_CommandIconDefault")<br />Ikona domyślna polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | N/d (dziedziczy tła paska poleceń) |
| Narzędzia (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Brak |

**Ikona polecenia: domyślny stan wybrane**

![Domyślnie, ikona wybranego polecenia](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br />Domyślnie, ikona wybranego polecenia  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarSelected` |
| Narzędzia (tekst) | `Environment.CommandBarTextSelected` |
| Obramowanie | `Environment.CommandBarSelectedBorder` |

**Ikona polecenia: stany przesuwania lub fokus**  

![Ikona polecenia przesuwania lub fokus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 025_CommandIconHover")<br />Ikona polecenia przesuwania lub fokus

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.CommandBarTextHover` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: stany przesuwania lub fokus wybrane**

![Wybrane polecenie ikonę na przesuwania lub fokus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br />Wybrane polecenie ikonę na przesuwania lub fokus

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarHoverOverSelected` |
| Narzędzia (tekst) | `Environment.CommandBarTextHoverOverSelected` |
| Obramowanie | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ikona polecenia: naciśnięty stanu**  

![Naciśnięto ikona polecenia](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 027_CommandIconPressed")<br />Ikona polecenia wciśnięty

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.CommandBarTextMouseDown` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: stanu wyłączonego**  

![Ikona polecenia wyłączenia](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 028_CommandIconDisabled")<br />Ikona polecenia wyłączone

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | N/d (dziedziczy tła paska poleceń) |
| Narzędzia (tekst) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |

####  <a name="BKMK_CommandComboBox"></a> Pola kombi pasek poleceń

> [!IMPORTANT]
> Pola kombi są podobne do listy rozwijane, ale obejmuje region tekst do edycji. Jeśli z listy rozwijanej nie obejmuje regionie można edytować tekst, Użyj kolorów tokeny zabezpieczające [polecenia paska listach rozwijanych](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  

![Polecenie superpaska pola kombi poprawek](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 029_ComboBoxRedline")<br />Pole kombi pasek poleceń (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas kompilowania pola kombi niestandardowych. | ... dla wszystkich elementów, nie ma zawsze odpowiadające polecenie Pasek interfejsu użytkownika. |
| ... podczas tworzenia formantu paska polecenie podobne do pola kombi. | ... Jeśli mają dostęp do pola kombi styl. |

**Pole wejściowe pole kombi paska poleceń: domyślna stanu**

![Pole wejściowe pole kombi paska poleceń](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 030_ComboBoxInputField")<br />Pole wejściowe pole kombi pasek poleceń  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxBackground` |
| Narzędzia (tekst) | `Environment.ComboBoxText` |
| Obramowanie | `Environment.ComboBoxBorder` |
| Separator | Nie separatora |

**Przycisk rozwijany pasek polecenia: domyślna stanu**  

![Upuść pole kombi&#45;klawisz](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br />Przycisk rozwijany pasek polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | N/d (dziedziczy tła paska poleceń) |
| Narzędzia (symbol) | `Environment.ComboBoxGlyph` |

**Polecenie paska menu rozwijanego: domyślna stanu**

![Polecenie paska menu rozwijanego](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br />Listy rozwijanej pasek poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxPopupBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.ComboBoxPopupBorder` |

**Pole wejściowe pole kombi paska poleceń: wskaźnika stanu**  

![Polecenie paska wejściowych polu kombi przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br />Polecenie paska wejściowych polu kombi przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.ComboBoxMouseOverText` |
| Obramowanie | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Przycisk rozwijany pasek polecenia: wskaźnika stanu**  

![Przycisk rozwijany pasek polecenia przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br />Przycisk rozwijany pasek polecenia przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseOverBackground` |
| Narzędzia (symbol) | `Environment.ComboBoxMouseOverGlyph` |

**Polecenie paska menu rozwijanego: wskaźnika stanu**

 ![Polecenie paska menu rozwijanego przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br />Polecenie paska menu rozwijanego przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tła (element Menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Narzędzia (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (element Menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pole wejściowe pole kombi paska poleceń: fokus stanu**  

![Fokus pasku pole wejściowe pole kombi poleceń](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br />Fokus pole wejściowe pole kombi pasek poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedBackground` |
| Narzędzia (tekst) | `Environment.ComboBoxFocusedText` |
| Obramowanie | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Przycisk rozwijany pasek polecenia: fokus stanu**  

![Polecenie paska przycisku rozwijanego fokus](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br />Polecenie ukierunkowanych, pasek przycisku rozwijanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedButtonBackground` |
| Narzędzia (symbol) | `Environment.ComboBoxFocusedGlyph` |

 **Pole wejściowe pole kombi paska poleceń: naciśnięty stanu**  

![Naciśnięciu polecenia paska pole wejściowe pole kombi](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br />Naciśnięto pole wejściowe pole kombi pasek poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseDownBackground` |
| Narzędzia (tekst) | `Environment.ComboBoxMouseDownText` |
| Obramowanie | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Przycisk rozwijany pasek polecenia: naciśnięty stanu**

![Naciśnięto pasku przycisku rozwijanego poleceń](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br />Naciśnięto pasku przycisku rozwijanego poleceń  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseDownBackground` |
| Narzędzia (symbol) | `Environment.ComboBoxMouseDownGlyph` |

**Pole wejściowe pole kombi paska poleceń: stanu wyłączonego**  

![Wyłączone pasku pole wejściowe pole kombi poleceń](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br />Polecenia wyłączonego paska pole wejściowe pola kombi  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxDisabledBackground` |
| Narzędzia (tekst) | `Environment.ComboBoxDisabledText` |
| Obramowanie | `Environment.ComboBoxDisabledBorder` |
| Separator | Nie separatora |

**Przycisk rozwijany pasek polecenia: stanu wyłączonego**  

![Wyłączone pasku przycisku rozwijanego poleceń](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br />Polecenie wyłączonego paska przycisku rozwijanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (symbol) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a> Rozwijane pasek poleceń

> [!IMPORTANT]
>  Listy rozwijane są podobne do pola kombi, ale brakuje regionów tekst do edycji. Jeśli z listy rozwijanej zawiera region można edytować tekst, Użyj kolorów tokeny zabezpieczające [polecenia superpaska pola kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  

![Pasek listy rozwijanej poleceń (poprawek)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 042_DropdownRedline")<br />Pasek listy rozwijanej poleceń (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia Kontrolki niestandardowe listy rozwijanej. | ... dla wszystkich elementów, które nie są podobne do listy rozwijanej. |
| | ... dla pola kombi lub Podziel przycisków. |   

**Pola wyboru z listy rozwijanej pasek poleceń: domyślna stanu**  

![Domyślnie polecenie paska pola wyboru z listy rozwijanej](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 043_DropdownSelectionField")<br />Pola wyboru z listy rozwijanej pasek polecenia domyślne  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownBackground` |
| Narzędzia (tekst) | `DropDownText` |
| Obramowanie | `DropDownBorder` |
| Separator | Nie separatora |

**Przycisk rozwijany pasek polecenia: domyślna stanu**

![Domyślnie polecenia paska przycisku rozwijanego](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 044_DropdownButton")<br />Rozwijany pasek przycisku domyślnego  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (symbol) | `Environment.DropDownGlyph` |

**Polecenie paska menu rozwijanego: domyślna stanu**

![Domyślnie polecenia paska menu rozwijanego](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 045_DropdownList")<br />Listy rozwijanej pasek poleceń domyślne  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownPopupBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.DropDownPopupBorder` |
| Cień | `Environment.DropShadowBackground` |

**Pola wyboru z listy rozwijanej pasek poleceń: wskaźnika stanu**  

![Pola wyboru z listy rozwijanej pasek poleceń przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br />Pola wyboru z listy rozwijanej pasek poleceń przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownMouseOverBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.DropDownMouseOverText` |
| Obramowanie | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Przycisk rozwijany pasek polecenia: wskaźnika stanu**  

![Przycisk rozwijany pasek polecenia przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br />Przycisk rozwijany pasek polecenia przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseOverBackground` |
| Narzędzia (symbol) | `Environment.DropDownMouseOverGlyph` |

**Polecenie paska menu rozwijanego: wskaźnika stanu**  

![Polecenie paska menu rozwijanego przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 048_DropdownListHover")<br />Polecenie paska menu rozwijanego przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tła (element Menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Narzędzia (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (element Menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pola wyboru z listy rozwijanej pasek poleceń: naciśnięty stanu**  

![Upuść&#45;w dół do pola wyboru naciśnięty](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br />Naciśnięto polecenia paska pola wyboru z listy rozwijanej

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownMouseDownBackground` |
| Narzędzia (tekst) | `Environment.DropDownMouseDownText` |
| Obramowanie | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Przycisk rozwijany pasek polecenia: naciśnięty stanu**

![Naciśnięto pasku przycisku rozwijanego poleceń](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br />Naciśnięto pasku przycisku rozwijanego poleceń  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseDownBackground` |
| Narzędzia (symbol) | `Environment.DropDownMouseDownGlyph` |

**Pola wyboru z listy rozwijanej pasek poleceń: stanu wyłączonego**  

![Wyłączone pasku pola wyboru z listy rozwijanej poleceń](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")<br />Polecenie wyłączonego paska pola wyboru z listy rozwijanej

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownDisabledBackground` |
| Narzędzia (tekst) | `Environment.DropDownDisabledText` |
| Obramowanie | `Environment.DropDownDisabledBorder` |
| Separator | Nie separatora |

**Przycisk rozwijany pasek polecenia: stanu wyłączonego**

![Wyłączone pasku przycisku rozwijanego poleceń](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")<br />Polecenie wyłączonego paska przycisku rozwijanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (symbol) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Pasek poleceń podzielić przycisków
Przyciski podziału udostępniać wiele nazw tokenu inne formanty paska poleceń, takich jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne akcji i nazwy tokenu przycisku rozwijanego są powtarzane tutaj dla wygody. Listy rozwijane przycisku podziału są implementacje [polecenia paska menu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  

![Przycisk podziału poprawek](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 053_SplitButtonRedline")<br />Przycisk podziału paska poleceń (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia przycisku podziału niestandardowych. | ... dla innych rodzajów przycisków. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Przycisk podziału paska poleceń: domyślna stanu**  

![Domyślny przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 054_SplitButton")<br />Pasek poleceń domyślny przycisk podziału  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (tekst) | `Environment.CommandBarTextActive` |
| Narzędzia (symbol) | `Environment.CommandBarSplitButtonGlyph` |
| Obramowanie | Brak |
| Separator | Brak |

**Przycisk podziału paska poleceń: wskaźnika stanu**  

![Przycisk przy aktywowaniu podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 055_SplitButtonHover")<br />Przycisk przy aktywowaniu podziału pasek poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.CommandBarTextHover` |
| Narzędzia (symbol) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Przycisk podziału paska poleceń: naciśnięty stanu**  

![Naciśnięty przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 056_SplitButtonPressed")<br />Pasek poleceń kliknięty przycisk podziału  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.CommandBarTextMouseDown` |
| Narzędzia (symbol) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | Brak |

**Przycisk podziału paska poleceń: stanu wyłączonego**

![Wyłączony przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br />Przycisk podziału wyłączonego paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (tekst) | `Environment.ComboBoxItemTextInactive` |
| Narzędzia (symbol) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |
| Separator | Brak |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Polecenie "Więcej opcji" i "Overflow" paska przycisków  
Przycisk "Więcej opcji" jest używany w przypadku grupy pasek poleceń można dostosowywać przez albo dodawanie lub usuwanie przycisków paska poleceniem. Przycisk "Overflow" jest wyświetlany, gdy pasek poleceń obcięte ze względu na Brak miejsca na poziomie, a następnie kliknij pokazuje menu zawierający przycisków paska poleceń nie może być wyświetlany. Kolory dla tych dwóch przycisków są kontrolowane przez ten sam zestaw nazw tokenów.  

![Polecenie paska przycisk "Więcej opcji" (poprawek)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 058_MoreOptionsRedline")<br />Polecenie paska przycisk "Więcej opcji" (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla niestandardowych "więcej opcji" lub "Overflow" przycisków. | ... w przypadku przycisków, które nie mają podobne funkcje do bardziej opcje lub przycisku "Overflow". |

**Polecenie Więcej opcji i ustawienie "Overflow" przycisków paska: domyślna stanu**  

![Domyślnie polecenie paska przycisk "Więcej opcji"](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 059_MoreOptions")<br />Przycisk "Więcej opcji" domyślne pasek poleceń

![Polecenie paska ustawienie "Overflow" przycisk domyślny](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 060_Overflow")<br />Domyślny przycisk "Overflow" pasek poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsBackground` |
| Narzędzia (symbol) | `Environment.CommandBarOptionsGlyph` |

**Polecenie Więcej opcji i ustawienie "Overflow" przycisków paska: wskaźnika stanu**

![Polecenie paska przycisk "Więcej opcji" przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 061_MoreOptionsHover")<br />Przycisk "Więcej opcji" przy aktywowaniu — pasek poleceń  

![Pasek ustawienie "Overflow" przycisku przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 062_OverflowOptions")<br />Pasek ustawienie "Overflow" przycisku przy aktywowaniu   

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (symbol) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Polecenie Więcej opcji i ustawienie "Overflow" przycisków paska: naciśnięty stanu**  

![Naciśnięto polecenia paska przycisk "Więcej opcji"](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 063_MoreOptionsPressed")<br />Naciśnięto polecenia paska przycisk wyświetlić więcej opcji  

![Przepełnienie naciśnięty](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 064_OverflowPressed")<br />Naciśnięty przycisk ustawienie "Overflow" pasek poleceń  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (symbol) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Okna dokumentów  
Ponieważ są one udostępniane przez środowisko Visual Studio jest niepotrzebna replikowanie okna dokumentów. Jednak można zdecydować, że chcesz wykorzystać kolory używane w systemie windows dokumentu, aby Twój interfejs użytkownika zawsze wyświetlany jest zgodne z tej części środowiska Visual Studio.  

Podczas korzystania z tokenów koloru okna dokumentu, należy zachować ostrożność z nich korzystać tylko dla podobnych elementów i zawsze w parach. Jeśli nie zrobisz może uzyskać nieoczekiwane wyniki w Interfejsie użytkownika.  

### <a name="document-window-frames"></a>Ramki okna dokumentu  
Okna dokumentów może być zadokowany w IDE lub przestawne jako osobne okno. Gdy okno dokumentu jest zmiennoprzecinkową poza IDE, on nadal znajduje się w dokumencie poprawnie i ma tła, obramowanie, tekst i kolory kart, które są takie same jak, gdy jest on częścią IDE. Jednak dokumentu znajduje się wewnątrz ramki, który ma swoją własną tła, obramowania i kolory tekstu. Narzędzia windows zadokowany w źródło dokumentu dziedziczą zachowanie i kolor ich karty z tokenu nazwy okna dokumentu.  

![Okno dokumentu zadokowanych (poprawek)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")<br />Okno dokumentu zadokowanych (poprawek)  

![Przestawne okno dokumentu (poprawek)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")<br />Przestawne okno dokumentu (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzeniu interfejsu użytkownika, które chcesz dopasować okno dokumentu. | dla elementów interfejsu użytkownika, które użytkownik chce automatycznie zmienić, jeśli powłoki ma... aktualizacji motywu. |

**Okno dokumentu zadokowane i przestawne: domyślna stanu**  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Zależy od typu dokumentu |
| Narzędzia (tekst) | Zależy od typu dokumentu |
| Obramowanie | `Environment.ToolWindowBorder` |

**Ukierunkowanych zmiennoprzecinkową ramki okna dokumentu: domyślna stanu**

![Domyślne fokus, zmiennoprzecinkową ramki okna dokumentu](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 067_FrameFocused")<br />Domyślne fokus, zmiennoprzecinkową ramki okna dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrame` |
| Narzędzia (tekst) | `Environment.ToolWindowFloatingFrame` |
| Narzędzia (symbol) | `Environment.RaftedWindowButtonActiveGlyph` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonActiveBorder`<br />(Ustaw przezroczysty) |

**Ramki okna dokumentu bez fokusu, zmiennoprzecinkowych: domyślna stanu**  

![Ramki okna bez fokusu, zmiennoprzecinkowych dokument domyślny](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 068_FrameUnfocused")<br />Domyślna ramki okna dokumentu bez fokusu, zmiennoprzecinkowych

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrameInactive` |
| Narzędzia (tekst) | `Environment.ToolWindowFloatingFrameInactive` |
| Narzędzia (symbol) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Ustaw przezroczysty) |

**Ukierunkowanych zmiennoprzecinkową ramki okna dokumentu: wskaźnika stanu**

![Ukierunkowanych zmiennoprzecinkową ramki okna dokumentów przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 069_FrameFocusedHover")<br />Ukierunkowanych zmiennoprzecinkową przy aktywowaniu ramki okna dokumentu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (symbol) | `Environment.RaftedWindowButtonHoverActive` |
| Narzędzia (symbol) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Ramki okna dokumentu bez fokusu, zmiennoprzecinkowych: wskaźnika stanu**  

![Ramki okna dokumentu bez fokusu, zmiennoprzecinkowych przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br />Bez fokusu, po umieszczeniu na liczby zmiennoprzecinkowe ramki okna dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (symbol) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Narzędzia (symbol) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Ukierunkowanych zmiennoprzecinkową ramki okna dokumentu: naciśnięty stanu**  

![Ukierunkowanych zmiennoprzecinkową ramki okna dokumentu na naciśnij](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 071_FrameFocusedPressed")<br />Ukierunkowanych zmiennoprzecinkową ramki okna dokumentu na naciśnij klawisz

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (symbol) | `Environment.RaftedWindowButtonDown` |
| Narzędzia (symbol) | `Environment.RaftedWindowButtonDownGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Karty dokumentów  
Karty dokumentów sit w kanale kartę, aby wskazać dokumenty, które są aktualnie otwarte, wraz z których jeden jest bieżącą wybrane lub aktywnego dokumentu. Narzędzia windows również może być zadokowany w kanale kartę dokumentu, jeśli użytkownik umieszcza je istnieje. W takiej sytuacji jako okna dokumentów przy użyciu takich samych kolorów karty. Są Tworzenie interfejsu użytkownika chcesz zawsze odpowiada kolory okno dokumentu (w tym motywu aktualizacji lub jeśli są zainstalowane kompozycje nowy), a następnie tokeny kolorów te odwołania.  

![Kart dokumentów (poprawek)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 072_DocumentTabRedline")<br />Kart dokumentów (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzeniu interfejsu użytkownika, które chcesz dopasować karty dokumentów i automatyczne pobranie aktualizacji motywu lub nowego motywu kolorów. | ... dla elementów interfejsu użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoki ma motyw aktualizacji. |

#### <a name="open-document-tabs"></a>Otwórz dokument karty  
Każdy otwarty dokument ma kartę w kanale kartę dokumentu, który wyświetla jego nazwę. Dokumenty mogą być wybrany lub Otwórz w tle, a ich karty odzwierciedlić te stany:  

-   Wybrana karta reprezentuje dokument, który jest aktualnie wyświetlany w dokumencie również. Wybrana karta ma obramowanie dokumentu, rozszerzający między górną krawędzią dokumentu oraz.  

-   Wszystkie karty dokumentów, które nie są aktualnie wybrana karta są karty tła. Po kliknięciu stają się wybranej karty i uzyskać wszystkie kolory tła, obramowania i tekst z tymi nazwami tokenu.  

![Karta otwartego dokumentu (poprawek)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")<br />Karta otwartego dokumentu (poprawek)

| Użyj...  | Nie używaj... |
| --- | --- |
| ... podczas tworzenia kart niestandardowych dokumentu. | ... dla kart tymczasowe (wersja zapoznawcza). |
| | dla elementów interfejsu użytkownika, których nie chcesz, aby zmienić automatycznie, jeśli powłoki ma... aktualizacji motywu. |

**Karta wybranych, konkretną dokumentu**  

![Zaznaczone, fokus dokumencie karta](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 074_SelectedTabFocused")<br />Karta wybranych, konkretną dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabSelectedGradientTop`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.FileTabSelectedText` |
| Obramowanie | `Environment.FileTabSelectedBorder`<br />(Ustaw kolor tła). |
| Obramowanie dokumentu | `Environment.FileTabDocumentBorderBackground` |

**Wybrane zakładkę bez fokusu**

![Wybrane zakładkę bez fokusu](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br />Wybrane zakładkę bez fokusu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabInactiveGradientTop`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.FileTabInactiveText` |
| Obramowanie | `Environment.FileTabInactiveBorder`<br />(Ustaw kolor tła). |
| Obramowanie dokumentu | `Environment.FileTabInactiveDocumentBorderBackground` |

**Tło dokumencie karta: domyślna stanu**  

![Domyślne tło dokumentu kartę](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 076_BackgroundTab")<br />Karta dokumentu tła domyślne  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabBackground` |
| Narzędzia (tekst) | `Environment.FileTabText` |
| Obramowanie | `Environment.FileTabBorder`<br />(Ustaw kolor tła). |

**Tło dokumencie karta: wskaźnika stanu**  

![Tła dokumencie karta przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 077_BackgroundTabHover")<br />Tła dokumencie karta przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabHotGradientTop`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.FileTabHotText` |
| Obramowanie | `Environment.FileTabHotBorder`<br />(Ustaw kolor tła). |

#### <a name="preview-tab"></a>Karta Podgląd  
Skrót kartę "tymczasowe". Na karcie Podgląd pojawia się po prawej stronie dokumencie karta kanału po kliknięciu elementu w Eksploratorze rozwiązań okna narzędzia. Zachowuje się jak podglądu dokumentu, a również zapewnia opcję pozostawienia dokument otwarty po lewej stronie kanał kartę dokumentu. Otwórz kartę Podgląd tylko jedna może być otwarty naraz. Podgląd karty ma zarówno w tle i wybranych stanów, takich jak karty i może być ukierunkowanych lub bez fokusu w ich stanie aktywnym.  

![Karta Podgląd (poprawek)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 078_PreviewTabRedline")<br />Karta Podgląd (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... gdziekolwiek tworzysz tymczasowego Podgląd i mają pewne elementu do dopasowania bieżący kolor tab podglądu. | ... dla każdego typu dokumentu lub kartę, która nie jest tymczasowe (wersja zapoznawcza). |
| | dla elementów interfejsu użytkownika, których nie chcesz, aby zmienić automatycznie, jeśli powłoki ma... aktualizacji motywu. |

**Karta Podgląd ukierunkowanych, wybrane**  

![Karta Podgląd ukierunkowanych, wybrane](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 079_PreviewTabFocused")<br />Karta Podgląd ukierunkowanych, wybrane

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedActive` |
| Narzędzia (tekst) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Ustaw kolor tła). |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Karta Podgląd bez fokusu, wybrane**  

![Karta Podgląd bez fokusu, wybrane](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br />Karta Podgląd bez fokusu, wybrane

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedInactive` |
| Narzędzia (tekst) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Karta Podgląd tła: domyślna stanu**  

![Karta Podgląd tła domyślne](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br />Karta Podgląd tła domyślne  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalInactive` |
| Narzędzia (tekst) | `Environment.FileTabProvisionalInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalInactiveBorder`<br />(Ustaw kolor tła). |

**Karta Podgląd tła: wskaźnika stanu**  

![Karta Podgląd tła przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br />Karta Podgląd tła przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalHover` |
| Narzędzia (tekst) | `Environment.FileTabProvisionalHoverForeground` |
| Obramowanie | `Environment.FileTabProvisionalHoverBorder`<br />(Ustaw kolor tła). |

#### <a name="document-overflow-button"></a>Przycisk przepełnienie dokumentu  
Przycisk przepełnienie dokument jest obecny, jeśli istnieje jeden lub więcej dokumentów otworzyć, niezależnie od tego, czy istnieje przestrzeń w pionie w bieżącej konfiguracji, aby dopasować wszystkich kart dokumentu. Menu rozwijane przepełnienie dokumentu, które są kontrolowane przez [polecenia menu paska](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) kolory, zostanie wyświetlona lista wszystkich otwartych dokumentów, zarówno widoczna i ukryta i zmiany symbolu przepełnienie w zależności od tego, czy są otwarte dokumenty wyświetlany w kanale kartę.  

![Przycisk przepełnienie dokument (poprawek)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 083_OverflowRedline")<br />Przycisk przepełnienie dokument (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia przycisku przeciążenia niestandardowego dokumentu. | ... dla interfejsu użytkownika, które nie są podobne do przycisku przeciążenia. |
| | ... dla przycisków przepełnienie paska poleceń. |

**Przycisk przepełnienie dokument: domyślna stanu**  

![Przycisk przepełnienie dokument domyślny](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 084_Overflow")<br />Przycisk przepełnienie dokument domyślny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonBackground` |
| Narzędzia (symbol) | `Environment.DocWellOverflowButtonGlyph` |
| Obramowanie | Brak |

**Przycisk przepełnienie dokument: wskaźnika stanu**

![Przycisk przepełnienie dokument przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 085_OverflowHover")<br />Przycisk przepełnienie dokument przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Narzędzia (symbol) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Przycisk przepełnienie dokument: naciśnięty stanu**  

![Przycisk przepełnienie dokument na naciśnij](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 086_OverflowPressed")<br />Przycisk przepełnienie dokument na naciśnij klawisz

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Narzędzia (symbol) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Znakowanie  
Program Visual Studio obsługuje znakowanie, który umożliwia użytkownikowi zadeklarować wyszukiwanie słów kluczowych na potrzeby śledzenia. Na przykład menedżerów i deweloperów można użyć Team Foundation Server (TFS) do znakowania elementów roboczych. W poniższych tabelach Nadaj nazwy kolorów dla samego tagu i symbolu "ikona Zamknij", aktywacji i wybranych stanów.  

![Znakowanie w programie Visual Studio (poprawek)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 176_TaggingRedline")<br />Znakowanie w programie Visual Studio (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla interfejsu użytkownika, który obsługuje znakowanie. | ... dla dowolnego innego typu interfejsu użytkownika. |

#### <a name="tags"></a>Znaczniki  

**Znacznik: stan domyślny**

![Znacznik domyślny](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 177_Tag")<br />Domyślny znacznik

| Element | Nazwa tokenu: Category.color |
| --- | --- |  
| Tło | `Tag.Background` |
| Narzędzia (tekst) | `Tag.Background` |

**Tag: stan aktywowanego**  

![Tag przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 178_TagHover")<br />Tag przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |  
| Tło | `Tag.HoverBackground` |
| Narzędzia (tekst) | `Tag.HoverBackgroundText` |

**Tag: stan naciśnięcia**

![Naciśnięto tag](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 179_TagPressed")<br />Tag wciśnięty  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.PressedBackground` |
| Narzędzia (tekst) | `Tag.PressedBackgroundText` |

**Tag: wybrany stan**

![Zaznaczony tag](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 180_TagSelected")<br />Wybrany tag  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.SelectedBackground` |
| Narzędzia (tekst) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Zamknij (&times;) tag symbolu

**Zamknij (&times;) tag symbolu: domyślna stanu**

![Domyślna Zamknij (&times;) tag symbolu](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 181_TagGlyph")<br />Domyślna Zamknij (&times;) tag symbolu

| Element | Nazwa tokenu: Category.color |
| --- | --- |  
| Tło | Brak |
| Narzędzia (symbol) | `Tag.TagHoverGlyph` |

**Zamknij (&times;) tag symbolu: wskaźnika stanu**

![Zamknij (&times;) tag symbolu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 182_TagGlyphHover")<br />Zamknij (&times;) tag symbolu przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphHoverBackground` |
| Narzędzia (symbol) | `Tag.TagHoverGlyphHover` |
| Obramowanie | `Tag.TagHoverGlyphHoverBorder` |

**Zamknij (&times;) tag symbolu: naciśnięty stanu**

![Naciśnięto Zamknij (&times;) tag symbolu](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 183_TagGlyphPressed")<br />Naciśnięto Zamknij (&times;) tag symbolu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphPressedBackground` |
| Narzędzia (symbol) | `Tag.TagHoverGlyphPressed` |
| Obramowanie | `Tag.TagHoverGlyphPressedBorder` |

**Zaznaczony tag z Zamknij (&times;) symbolu: domyślna stanu**

![Domyślnie wybrany tag z Zamknij (&times;) symbolu](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 184_TagSelected")<br />Domyślnie wybrany tag z Zamknij (&times;) symbolu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (symbol) | `Tag.TagSelectedGlyph` |

**Zaznaczony tag z Zamknij (&times;) symbolu: wskaźnika stanu**  

![Zaznaczony tag z Zamknij (&times;) symbolu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 185_TagSelectedHover")<br />Zaznaczony tag z Zamknij (&times;) symbolu przy aktywowaniu  


| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphHoverBackground` |
| Narzędzia (symbol) | `Tag.TagSelectedGlyphHover` |
| Obramowanie | `Tag.TagSelectedGlyphHoverBorder` |

**Zaznaczony tag z Zamknij (&times;) symbolu: naciśnięty stanu**  

![Zaznaczone, naciśnięciu tag z Zamknij (&times;) symbolu](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 186_TagSelectedPressed")<br />Zaznaczone, naciśnięciu tag z Zamknij (&times;) symbolu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphPressedBackground` |
| Foreground(Glyph) | `Tag.TagSelectedGlyphPressed` |
| Obramowanie | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Okna narzędzi  
Ponieważ są one udostępniane przez środowisko Visual Studio jest niepotrzebna replikowanie okna narzędzi. Jednak można zdecydować, że chcesz wykorzystać kolory używane w narzędzia windows tak, aby Twój interfejs użytkownika zawsze wyświetlany jest zgodne z tej części środowiska Visual Studio.  

![Okno narzędzia (poprawek)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 087_ToolWindowRedline")<br />Okno narzędzia (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzeniu interfejsu użytkownika, które chcesz dopasować okna narzędzi. | dla elementów interfejsu użytkownika, których nie chcesz, aby zmienić automatycznie, jeśli powłoki ma... aktualizacji motywu. |

### <a name="tool-window-frame"></a>Ramki okna narzędzi  
Narzędzia systemu windows w programie Visual Studio są używane do wielu zadań i może występować w jednym z kilku różnych stanach. Jeśli okno narzędzia jest otwarty, można go przypisać do dowolnego z czterech stron obszaru dokumentu. Narzędzia systemu windows można także float poza IDE, która umożliwia im to można zmienić ich pozycji dowolne miejsce w obrębie ekranu użytkownika. Przestawne systemu windows zawsze znajdują się na szczycie IDE. Na koniec narzędzia windows może być zadokowany jako okna dokumentów i są wyświetlane na karcie w dokumencie dobrze. Narzędzia systemu windows, które zostało zadokowane jako okna dokumentów są kolorowe częściowo przy użyciu nazwy tokenu okno dokumentu.  

![Ramki okna narzędzia (poprawek)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")<br />Ramki okna narzędzia (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzeniu interfejsu użytkownika, które chcesz dopasować okna narzędzi. | dla elementów interfejsu użytkownika, których nie chcesz, aby zmienić automatycznie, jeśli powłoki ma... aktualizacji motywu. |

**Okno narzędzia zadokowanych**  

![Okno narzędzia zadokowanych](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 089_ToolWindowDocked")<br />Okno narzędzia zadokowanych  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.ToolWindowBorder` |

**Przestawne, fokus okna narzędzi**

![Przestawne, fokus okna narzędzia](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 090_ToolWindowFocused")<br />Przestawne, fokus okna narzędzi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |

**Przestawne okna narzędzia bez fokusu**  

![Okno narzędzia przestawne, bez fokusu](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 091_ToolWindowUnfocused")<br />Przestawne okna narzędzia bez fokusu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Windows przypominającej przybornika
Przybornik jest jednym z najczęściej używanych typowe narzędzia systemu windows w programie Visual Studio. Jest zasadniczo formantu drzewa o specjalne motywu i stylów zastosowana.  

![Okno przybornika przypominającej (poprawek)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 189_ToolboxRedline")<br />Okno przybornika przypominającej (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas projektowania okna narzędzia, która ma być zgodne z przybornika powłoki. | ... dla wszystkich elementów, które nie są podobne do przybornika interfejsu użytkownika lub jeśli nie wiesz, czy interfejsu użytkownika będzie mieć problemy, jeśli zmiana kolorów przybornika powłoki. |

**Węzły przybornika: domyślna stanu**

![Węzeł nadrzędny domyślnego przybornika](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 190_ToolboxParentNode")<br />Węzeł nadrzędny domyślnego przybornika

![Węzeł podrzędny domyślnego przybornika](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 191_ToolboxChildNode")<br />Węzeł podrzędny domyślnego przybornika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolboxContent`<br />(Nagłówki) |
| Tło | `Environment.ToolWindowBackground`<br />(Pojedynczych elementów lub całe okno, jeśli żadne formanty dostępne) |
| Obramowanie | Brak |
| Narzędzia (symbol) | `Environment.ToolboxContent` |
| Narzędzia (tekst) | `Environment.ToolboxContent` |

**Węzły podrzędne przybornika: wskaźnika stanu**

![Węzeł podrzędny przybornika przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br />Węzeł podrzędny przybornika przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolboxContentMouseOver`<br />(Tylko w poszczególnych elementów) |
| Obramowanie | Brak |
| Narzędzia (tekst) | `Environment.ToolboxContentMouseOver`<br />(Tylko w poszczególnych elementów) |

**Wybrane węzły przybornika: fokus stanu**

![Węzeł nadrzędny przybornika ukierunkowanych, wybrane](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br />Węzeł nadrzędny ukierunkowanych, wybrane przybornika  

![Przybornik ukierunkowanych, wybranego węzła podrzędnego](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br />Przybornik ukierunkowanych, wybranego węzła podrzędnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive`<br />Z [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Obramowanie | `TreeView.FocusVisualBorder`<br />Z [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Narzędzia (symbol) | `TreeView.SelectedItemActive`<br />Z [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Narzędzia (tekst) | `TreeView.SelectedItemActive`<br />Z [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |

**Wybrane węzły przybornika: stanu bez fokusu**

![Węzeł nadrzędny wybranego, bez fokusu przybornika](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br />Węzeł nadrzędny przybornika wybrane, bez fokusu  

![Węzeł podrzędny przybornika wybrane, bez fokusu](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br />Węzeł podrzędny przybornika wybrane, bez fokusu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive`<br />Z [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Obramowanie | Brak |
| Narzędzia (symbol) | `TreeView.SelectedItemInactive`<br />Z [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Narzędzia (tekst) | `TreeView.SelectedItemInactive`<br />Z [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |

### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzi  
Wartość true, obramowanie nie jest obramowania paska tytułu, jest grubości linii w górnej części paska tytułu. Nie ma tokenu nazwę stanu bez fokusu.  

![Pasek tytułu okna narzędzia (poprawek)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")<br />Pasek tytułu okna narzędzia (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzeniu interfejsu użytkownika, które chcesz dopasować okna narzędzi. | dla elementów interfejsu użytkownika, których nie chcesz, aby zmienić automatycznie, jeśli powłoki ma... aktualizacji motywu. |

**Pasek tytułu mającego fokus**

![Pasek tytułu ukierunkowanych](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 093_TitleBarFocused")<br />Pasek tytułu mającego fokus

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.TitleBarActiveGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.TitleBarActiveText` |
| Obramowanie | `Environment.TitleBarActiveBorder`<br />(Ustaw kolor tła). |
| Przeciągnij uchwyt | `Environment.TitleBarDragHandleActive` |

**Pasek tytułu bez fokusu**  

![Pasek tytułu bez fokusu](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 094_TitleBarUnfocused")<br />Pasek tytułu bez fokusu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.TitleBarInactiveGradientBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.TitleBarInactiveText` |
| Obramowanie | Brak |
| Przeciągnij uchwyt | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Przyciski paska tytułu okna narzędzi  
![Tytuł paska przycisk (poprawek)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")<br />Tytuł paska przycisk (poprawek)  

| Użyj... | Nie używaj... |
| --- | --- |
| ... w przypadku przycisków, które są widoczne w interfejsu użytkownika, który korzysta z tokenów koloru z pasków tytułu okna narzędzi. | ... w przypadku przycisków, które są widoczne w innych lokalizacjach. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Fokus przycisków paska tytułu: domyślna stanu**

![Domyślnie, fokus przycisków paska tytułu](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br />Domyślnie przycisków paska tytułu mającego fokus  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (symbol) | `Environment.ToolWindowButtonActiveGlyph` |
| Obramowanie | Brak |

**Przyciski paska tytułu bez fokusu: domyślna stanu**

![Domyślnie, przycisków paska tytułu bez fokusu](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br />Domyślnie przycisków paska tytułu bez fokusu    

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Narzędzia (symbol) | `Environment.ToolWindowButtonInactiveGlyph` |
| Obramowanie | Brak |

**Fokus przycisków paska tytułu: wskaźnika stanu**  

![Fokus przycisków paska tytułu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br />Przyciski paska tytułu ukierunkowanych przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverActive` |
| Narzędzia (symbol) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverActiveBorder` |

**Przyciski paska tytułu bez fokusu: wskaźnika stanu**  

![Przyciski paska tytułu bez fokusu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br />Przyciski paska tytułu bez fokusu przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverInactive` |
| Narzędzia (symbol) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Fokus przycisków paska tytułu: naciśnięty stanu**

![Fokus na naciśnięcie przycisków paska tytułu](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br />Przyciski paska tytułu ukierunkowanych na naciśnij klawisz

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Narzędzia (symbol) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

**Przyciski paska tytułu bez fokusu: naciśnięty stanu**

![Przyciski paska tytułu bez fokusu na naciśnij](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br />Przyciski paska tytułu bez fokusu na naciśnij klawisz  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Narzędzia (symbol) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Karty okna narzędzi  
![Karta okna narzędzia (poprawek)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 102_ToolWindowTabRedline")<br />Karta okna narzędzia (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzeniu interfejsu użytkownika, które chcesz dopasować okna narzędzi. | dla elementów interfejsu użytkownika, których nie chcesz, aby zmienić automatycznie, jeśli powłoki ma... aktualizacji motywu. |

**Karta okna narzędzia wybranych, konkretną**

![Wybrano, fokus karta okna narzędzia](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br />Karta okna narzędzia wybranych, konkretną

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Narzędzia (tekst) | `Environment.ToolWindowTabSelectedActiveText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustaw kolor tła). |

**Karta okna narzędzia wybrane, bez fokusu**  

![Karta okna narzędzia wybrane, bez fokusu](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br />Karta okna narzędzia wybrane, bez fokusu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Narzędzia (tekst) | `Environment.ToolWindowTabSelectedText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustaw kolor tła). |

**Karta okna narzędzia tła: domyślna stanu**

![Karta okna narzędzia tła domyślne](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br />Karta okna narzędzia tła domyślne  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Gradientu zatrzymuje ustawioną taką samą wartość koloru w programie Visual Studio 2013). |
| Narzędzia (tekst) | `Environment.ToolWindowTabText` |
| Obramowanie | `Environment.ToolWindowTabBorder` |

**Karta okna narzędzia tła: wskaźnika stanu**

![Karta okna narzędzia tła przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br />Karta okna narzędzia tła przy aktywowaniu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Gradientu zatrzymuje ustawioną taką samą wartość koloru w programie Visual Studio 2013). |
| Narzędzia (tekst) | `Environment.ToolWindowTabMouseOverText` |
| Obramowanie | `Environment.ToolWindowTabMouseOverBorder`<br />(Ustaw kolor tła). |  

### <a name="auto-hide-tabs"></a>Automatyczne ukrywanie karty  

![Automatyczne ukrywanie karty (poprawek)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")karty autoukrywania (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzeniu interfejsu użytkownika, które chcesz dopasować karty okna ukryte automatycznie narzędzi. | dla elementów interfejsu użytkownika, których nie chcesz, aby zmienić automatycznie, jeśli powłoki ma... aktualizacji motywu. |

**Automatyczne ukrywanie kart: domyślna stanu**  

![Karta autoukrywania domyślne](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 108_AutoHideTab")<br />Karta autoukrywania domyślne

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.AutoHideTabBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.AutoHideTabText` |
| Obramowanie | `Environment.AutoHideTabBorder` |

**Automatyczne ukrywanie kart: wskaźnika stanu**

![Karta autoukrywania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 109_AutoHideTabHover")<br />Karta autoukrywania przy aktywowaniu  

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Narzędzia (tekst) | `Environment.AutoHideTabMouseOverText` |
| Obramowanie | `Environment.AutoHideTabMouseOverBorder` |
