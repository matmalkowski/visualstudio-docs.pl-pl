---
title: Jak utworzyć i zastosować zasobu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60b832e1c4b1834e35cc2ab6427b2686f5d730a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-and-apply-a-resource"></a>Jak utworzyć i zastosować zasobu
Szablony elementów w Projektancie XAML i style są przechowywane w wielokrotnego użytku jednostek nazywanych zasobów. Style umożliwiają ustawianie właściwości elementu i ponowne użycie tych ustawień, aby uzyskać spójny wygląd przez wiele elementów. A [ControlTemplate](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) określa wygląd formantu i mogą być również stosowane jako zasób. Aby uzyskać więcej informacji, zobacz [Szybki Start: formanty stylów](http://go.microsoft.com/fwlink/?LinkID=248239) i [Szybki Start: kontrolować szablony](http://go.microsoft.com/fwlink/?LinkID=247982).  
  
 Podczas tworzenia nowego zasobu z istniejącej właściwości [styl](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx), lub `ControlTemplate`, **tworzenie zasobu** okno dialogowe umożliwia zdefiniowanie zasobów na poziomie aplikacji, poziomie dokumentu lub na poziomie elementu. Te poziomy określają, których można użyć tego zasobu. Na przykład w przypadku definiowania zasobów na poziomie elementu, zasób może odnosić się tylko do elementu, na którym został utworzony. Istnieje również możliwość przechowywania zasobu w słowniku zasobów, oddzielnym pliku, który można użyć ponownie w innym projekcie.  
  
### <a name="to-create-a-new-resource"></a>Aby utworzyć nowy zasób  
  
1.  Plik XAML jest otwarty w Projektancie XAML Utwórz element, lub wybierz element w okno konspektu dokumentu.  
  
2.  W oknie właściwości wybierz znacznik właściwości, która jest wyświetlana jako symbol pola na prawo od wartości właściwości, a następnie wybierz **Konwertuj na nowy zasób**. Symbol biała Skrzynka wskazuje wartość domyślną, a symbol czarne pole zwykle wskazuje zastosowano zasobu lokalnego  
  
     Pojawi się odpowiednie okno dialogowego dla tworzenia zasobu. To okno dialogowe pojawia się po utworzeniu zasobu z pędzla:  
  
     ![Utwórz zasób — okno dialogowe](../designers/media/xaml_create_resource.png "xaml_create_resource")  
  
3.  W **nazwę (klucz)** wprowadź nazwę klucza. Jest to nazwa, pomocne, jeśli chcesz, aby inne elementy, które odwołują się do zasobu.  
  
4.  W obszarze **zdefiniować w**, wybierz opcję, która określa, gdzie zasobów do zdefiniowania:  
  
    -   Aby udostępnić zasobu dowolnych dokumentów w aplikacji, wybierz pozycję **aplikacji**.  
  
    -   Aby udostępnić zasobu do bieżącego dokumentu, wybierz **tego dokumentu**.  
  
    -   Aby udostępnić zasobu tylko element z której utworzono zasób lub jego elementów podrzędnych, wybierz pozycję **tego dokumentu**, a na liście rozwijanej wybierz *elementu*: *nazwa* .  
  
    -   Aby zdefiniować zasobu w pliku słownika zasobów, które mogą być ponownie używane w innych projektach, kliknij przycisk **słownik zasobów**, a następnie wybierz istniejący plik słownika zasobów, takich jak **StandardStyles.xaml**, na liście rozwijanej.  
  
5.  Wybierz **OK** przycisk, aby utworzyć zasobu i zastosować je do elementu, z którego został utworzony.  
  
### <a name="to-apply-a-resource-to-an-element-or-property"></a>Aby zastosować zasobu do elementu lub właściwości  
  
1.  Okno konspektu dokumentu wybierz element, który chcesz zastosować do zasobu.  
  
2.  Wykonaj jedną z następujących czynności:  
  
    -   Zastosuj zasobu do właściwości. W oknie Właściwości Wybieranie znacznik właściwości obok wartości właściwości, **zasobu lokalnego** lub **zasób systemowy**, a następnie wybierz z listy dostępnych zasobów.  
  
         Jeśli nie widzisz z zasobem, który można było się spodziewać, może to być, ponieważ typ zasobu jest niezgodny z typem właściwości.  
  
    -   Stosowanie zasobu szablon stylu lub formant do formantu. Wybierz menu kontekstowe kontrolki w oknie konspekt dokumentu, otwórz **Edytuj szablon** lub **Edytuj dodatkowe szablony**, wybierz **zastosować zasobów**, a następnie wybierz pozycję Nazwa szablonu formantu z wyświetlonej listy.  
  
        > [!NOTE]
        >  **Edytuj szablon** służy do stosowania szablonów kontrolki. **Edytuj dodatkowe szablony** służy do stosowania innych typów szablonu.  
  
     Zasoby może odnosić się tam, gdzie są one zgodne. Na przykład zasób pędzla można zastosować do **pierwszego planu** właściwość <xref:Windows.UI.Xaml.Controls.TextBox> formantu.  
  
### <a name="to-edit-a-resource"></a>Aby edytować zasobu  
  
1.  Wybierz element w obszarze roboczym lub w oknie konspektu dokumentu.  
  
2.  Wybierz znacznik właściwości domyślnej lub lokalnej z prawej strony właściwości w oknie właściwości, a następnie wybierz **edytowanie zasobów** otworzyć **edytowanie zasobów** okno dialogowe.  
  
3.  Modyfikowanie opcji dla zasobu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)