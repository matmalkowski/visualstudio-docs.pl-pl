---
title: 'Porady: dostęp do wbudowanych czcionek i schemat kolorów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1f329464b37d9b7de037523735cc09ff95dce3bd
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Porady: dostęp do wbudowanych czcionek i schemat kolorów
Visual Studio zintegrowane środowisko programistyczne (IDE) zawiera schemat czcionek i kolorów, który jest skojarzony z okna edytora. Można uzyskać dostęp za pośrednictwem systemu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu.

 Aby użyć wbudowanych czcionek i kolorów schematu, pakiet VSPackage musi:

-   Definiowanie kategorii do użycia z usługą czcionki i kolory domyślne.

-   Zarejestruj kategorii z domyślnego serwera czcionek i kolorów.

-   Zalecamy IDE, że określone okno używa wbudowanego wyświetlania elementów i kategorie przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfejsów.

 IDE używa wynikowy kategorii jako dojścia do okna. Nazwa kategorii jest wyświetlany w **Pokaż ustawienia dla:** pola rozwijanego w **czcionki i kolory** strony właściwości.

### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Aby zdefiniować kategorię przy użyciu wbudowanych czcionek i kolorów

1.  Utwórz dowolne identyfikatora GUID.

     Ten identyfikator GUID jest używany do jednoznacznego identyfikowania kategorię**.** Ta kategoria ponownie używa IDE domyślnej czcionki i kolory specyfikacji.

    > [!NOTE]
    >  Podczas pobierania danych czcionek i kolorów za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> lub inne interfejsy VSPackages za pomocą tego identyfikatora GUID wbudowanych informacje referencyjne.

2.  Nazwa kategorii należy dodać do tabeli ciągów w pliku zasobów (.rc) pakiet VSPackage, dzięki czemu można lokalizować zgodnie z potrzebami wyświetlanym w IDE.

     Aby uzyskać więcej informacji, zobacz [Dodawanie lub usuwanie ciągu](/cpp/windows/adding-or-deleting-a-string).

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Aby zarejestrować kategorię przy użyciu wbudowanych czcionek i kolorów

1.  Utworzyć specjalny typ wpisu rejestru kategorii w następującej lokalizacji:

     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio version>*\FontAndColors\\*\<Category>*]

     *\<Kategoria >* niezlokalizowana nazwa kategorii.

2.  Wypełnij rejestr, aby używać standardowych czcionek i kolorów schematu z cztery wartości:

    |Nazwa|Typ|Dane|Opis|
    |----------|----------|----------|-----------------|
    |Kategoria|REG_SZ|Identyfikator GUID|Dowolnego GUID, który określa kategorię, która zawiera podstawowe schematu czcionek i kolorów.|
    |Package|REG_SZ|Identyfikator GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Ten identyfikator GUID jest używany przez wszystkie pakiety VSPackage używających domyślne konfiguracje czcionek i kolorów.|
    |NameID|REG_DWORD|ID|Identyfikator zasobu nazwy kategorii Lokalizowalny w pakiecie VSPackage.|
    |ToolWindowPackage|REG_SZ|Identyfikator GUID|Identyfikator GUID wykonawczych pakiet VSPackage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu.|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Aby zainicjować stosowania dostarczane przez system czcionki i kolory

1.  Utwórz wystąpienie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfejsu jako część wdrożenia i inicjowania okna.

2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodę, aby uzyskać wystąpienia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfejsu odpowiadającego danego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> wystąpienia.

3.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> dwa razy.

    -   Wywołaj raz z `VSEDITPROPID_ViewGeneral_ColorCategory`jako argument.

    -   Wywołaj raz z `VSEDITPROPID_ViewGeneral_FontCategory` jako argument.

     Spowoduje to i udostępnia usługi czcionki i kolory domyślne jako właściwość okna.

## <a name="example"></a>Przykład
 Poniższy przykład powoduje zainicjowanie użycie wbudowanego czcionek i kolorów.

```cpp
CComVariant vt;
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);
if (spPropCatContainer != NULL){
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,
                                                          &spPropContainer))){
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Używanie czcionek i kolorów](../extensibility/using-fonts-and-colors.md)
- [Pobieranie czcionek i kolorów informacje dotyczące tekstu kolorowania](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Dostęp do przechowywanej czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md)
- [Omówienie kolorów i czcionek](../extensibility/font-and-color-overview.md)