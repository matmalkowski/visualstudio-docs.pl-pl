---
title: "Widoki pojedynczych i wielu kartę | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f20e5d251d8d6ef31289fb1b9ee8b9420ff9146a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="single-and-multi-tab-views"></a>Jedno- i kartę wielu widoków
Edytor tworzyć różne typy widoków. Przykładem jest okna edytora kodu, jest inny Projektant formularzy.  
  
 Widok z wieloma kartami jest widoku, który ma wiele kart. Na przykład edytora HTML ma dwie karty u dołu: **projekt** i **źródła**, każdy widok logiczny. Widok projektu wyświetla renderowanej strony sieci web, podczas gdy druga Wyświetla kod HTML, który obejmuje strony sieci web.  
  
## <a name="accessing-physical-views"></a>Uzyskiwanie dostępu do widoków fizycznych  
 Widoki fizyczne hosta obiekty widoku dokumentu, reprezentujący widok danych w buforze, takie jak kod lub formularz. W związku z tym każdy obiekt widoku dokumentu ma widoku fizycznego (określone przez czegoś znanego jako ciąg widoku fizycznego), a zazwyczaj pojedynczego widoku logicznym.  
  
 Jednak w niektórych przypadkach widoku fizycznego może mieć co najmniej dwa logiczne widoków. Oto kilka przykładów edytora z okna podziału z widokami side-by-side lub projektanta formularzy, który ma widoku graficznego interfejsu użytkownika/projekt i kod za-widoku formularza.  
  
 Aby włączyć edytora uzyskać dostęp do wszystkich dostępnych widoków fizycznych, należy utworzyć ciąg widoku fizycznego unikatowy dla każdego typu obiektu widoku dokumentu, który może tworzyć fabryką edytora. Na przykład [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] fabryki edytora może utworzyć dokumentu obiekty w widoku okna kodu i okno projektanta formularzy.  
  
## <a name="creating-multi-tabbed-views"></a>Tworzenie widoków z wieloma kartami  
 Mimo że obiekt widoku dokumentu musi być skojarzony z widoku fizycznego za pośrednictwem widoku fizycznego unikatowy ciąg, możesz umieścić wielu kart fizycznych widoku umożliwia wyświetlanie danych w różny sposób. W tej konfiguracji z wieloma kartami wszystkie karty są skojarzone z tych samych parametrach widoku fizycznego, ale każda karta znajduje się inny widok logiczny identyfikator GUID.  
  
 Aby utworzyć widok z wieloma kartami edytora, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> interfejs, a następnie skojarzyć inny widok logiczny identyfikator GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) z każdej karcie tworzenia.  
  
 Edytor programu Visual Studio HTML jest przykładem edytor z widoku wielu kartę. Ma ona **projekt** i **źródła** karty. Aby je włączyć, inny widok logiczny jest skojarzony z każdej karcie `LOGICALVIEWID_TextView` dla **projekt** kartę i `LOGICALVIEWID_Code` dla **źródła** kartę.  
  
 Określając odpowiedni widok logiczny pakiet VSPackage mają dostęp do widoku, która odnosi się do określonego celu, takie jak projektowania formularza, edytowanie kodu lub debugowanie kodu. Jednak jeden z systemu windows musi być identyfikowany przez ciąg NULL i to musi odpowiadać głównej widok logiczny (`LOGVIEWID_Primary`).  
  
 W poniższej tabeli wymieniono wartości dostępny widok logiczny i ich użycia.  
  
|IDENTYFIKATOR GUID LOGVIEWID|Zalecane użycie|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Widok domyślny/podstawowej fabryki edytora.<br /><br /> Wszystkie fabryki edytora musi obsługiwać tę wartość. Ten widok, musisz użyć pusty ciąg jako jego ciągu widoku fizycznego. Ta wartość musi wynosić co najmniej jeden widok logiczny.|  
|`LOGVIEWID_Debugging`|Debugowanie widoku. Zazwyczaj `LOGVIEWID_Debugging` mapy do tego samego widoku `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Wyświetl uruchomione przez **kod widoku** polecenia.|  
|`LOGVIEWID_Designer`|Wyświetl uruchomione przez **Wyświetl formularz** polecenia.|  
|`LOGVIEWID_TextView`|Widoku edytora tekstu. Jest to widok, który zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, z którego można uzyskać dostęp <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Monituje użytkownika o wybierz, którego widoku do użycia.|  
|`LOGVIEWID_ProjectSpecificEditor`|Przekazany przez **Otwórz za pomocą** okno dialogowe, aby<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> gdy użytkownik wybierze wpis "(Projekt domyślny edytor)".|  
  
 Chociaż widok logiczny identyfikatory GUID można rozszerzać, można użyć tylko widok logiczny identyfikatory GUID zdefiniowane w pakiecie VSPackage.  
  
 Podczas zamykania Visual Studio zachowuje identyfikator GUID fabryki edytora i ciągi widoku fizycznego skojarzony z oknem dokumentu, dzięki czemu można ponownie otworzyć okna dokumentów po ponownym otwarciu rozwiązania. Tylko systemu windows, które są otwarte po zamknięciu rozwiązania są zachowywane w pliku rozwiązania (.suo). Te wartości odpowiadają `VSFPROPID_guidEditorType` i `VSFPROPID_pszPhysicalView` wartości przekazane `propid` parametru w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody.  
  
## <a name="example"></a>Przykład  
 Ta Wstawka kodu ilustruje sposób <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> obiekt jest używany na dostęp do widoku, który implementuje `IVsCodeWindow`. W takim przypadku <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> usługi są używane do wywoływania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> i żądania `LOGVIEWID_TextView`, która uzyskuje wskaźnik do ramki okna. Wskaźnik do obiektu widoku dokumentu są uzyskiwane przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> i określając wartość `VSFPROPID_DocView`. Z obiektem widoku dokumentu `QueryInterface` jest wywoływana dla `IVsCodeWindow`. Oczekuje się w tym przypadku jest zwracany w edytorze tekstu, czy tak zwrócony obiekt widoku dokumentu w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metoda jest okna kodu.  
  
```cpp  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Porady: dołączanie widoków danych dokumentów](../extensibility/how-to-attach-views-to-document-data.md)   
 [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)