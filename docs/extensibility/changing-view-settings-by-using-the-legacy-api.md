---
title: Zmiana ustawień widoku przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc68bf5f8a0e61b80200cd5454b78bcdda78cdfe
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Zmiana ustawień widoku przy użyciu interfejsu API starsza wersja
Ustawienia podstawowe funkcje edytora, takie jak zawijanie, margines zaznaczania i wirtualną przestrzeń, można zmienić przez użytkownika przez **opcje** okno dialogowe. Jednak istnieje również możliwość zmiany tych ustawień programowo.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Zmiana ustawień za pomocą starszego interfejsu API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Interfejsu opisuje zestaw właściwości edytora tekstu. Wyświetl tekst zawiera kategorię właściwości (GUID_EditPropCategory_View_MasterSettings), która reprezentuje grupę programowo zmienionych ustawień widoku tekstu. Po Wyświetl ustawienia zostały zmienione w ten sposób, nie można zmienić w **opcje** okno dialogowe, dopóki nie dochodzi do zresetowania.  
  
 Oto typowy proces zmiany ustawień widoku wystąpienia edytora core.  
  
1.  Wywołanie `QueryInterface` na (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfejsu.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metody, określając wartość GUID_EditPropCategory_View_MasterSettings dla `rguidCategory` parametru.  
  
     W ten sposób zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfejsu, zawierający zestaw właściwości wymuszone dla widoku. Wszystkie ustawienia w tej grupie są stale wymuszone. Jeśli to ustawienie nie jest w tej grupie, a następnie będzie przestrzegany opcje określone w **opcje** okno dialogowe lub poleceń użytkownika.  
  
3.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metody, określając wartość odpowiednie ustawienia w `idprop` parametru.  
  
     Na przykład aby wymusić Zawijanie, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> i określ wartość VSEDITPROPID_ViewLangOpt_WordWrap, `vt` dla `idprop` parametru. W tym wywołaniu `vt` jest wariant typu VT_BOOL i `vt.boolVal` jest VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Resetowanie ustawienia zmiany widoku  
 Aby zresetować wszystkie zmiany widoku dla wystąpienia edytora podstawowe, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> — metoda i określ jej wartość odpowiednie ustawienie w `idprop` parametru.  
  
 Na przykład, aby umożliwić zawijanie można dowolnie przesuwać, należy usunąć go z kategorii właściwości przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> i określenie wartości VSEDITPROPID_ViewLangOpt_WordWrap dla `idprop` parametru.  
  
 Aby usunąć wszystkie zmienione ustawienia edytora rdzeni na raz, określ wartość VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt dla `idprop` parametru. W tym wywołaniu vt jest wariant typu VT_BOOL i vt.boolVal jest VARIANT_TRUE.  
  
## <a name="see-also"></a>Zobacz też  
 [W edytorze Core](../extensibility/inside-the-core-editor.md)   
 [Uzyskiwanie dostępu do theText widoku przy użyciu interfejsu API starsza wersja](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Opcje, okno dialogowe](../ide/reference/options-dialog-box-visual-studio.md)