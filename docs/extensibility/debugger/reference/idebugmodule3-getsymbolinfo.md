---
title: IDebugModule3::GetSymbolInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8648e591e545db73b636c6b21fcbcaa1d1afb640
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Pobiera listę ścieżek, które są wyszukiwane symboli, a także wyniki wyszukiwania poszczególnych ścieżek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```csharp  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Kombinacja flag z [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) wyliczenie opisujące który pola `pInfo` mają zostać wypełnione.  
  
 `pInfo`  
 [out] A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) struktury, której członkami są wypełnia się określone informacje. Jeśli jest to wartość null, ta metoda zwraca `E_INVALIDARG`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
>  Zwracany ciąg (w `MODULE_SYMBOL_SEARCH_INFO` struktury) może być pusta nawet wtedy, gdy `S_OK` jest zwracany. W takim przypadku nie było żadnych informacji wyszukiwania do zwrócenia.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `bstrVerboseSearchInfo` pole `MODULE_SYMBOL_SEARCH_INFO` struktury nie jest pusty, a następnie znajduje się lista ścieżek przeszukiwane i wyniki tego wyszukiwania. Lista jest sformatowany w systemie ścieżkę, a następnie wielokropkiem ("..."), a następnie wynik. Jeśli istnieje więcej niż jedna para wyników ścieżki, następnie każda para jest oddzielona parę "\r\n" (karetki return/wysuw wiersza). Wzorzec wygląda następująco:  
  
 \<Ścieżka >... \<wyniku > \r\n\<ścieżka >... \<wyniku > \r\n\<ścieżka >... \<wyniku >  
  
 Należy pamiętać, że ostatni wpis nie ma sekwencji \r\n.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie ta metoda zwraca trzy ścieżki na trzy inne wyniki wyszukiwania. Każdy wiersz jest przerywane przy użyciu pary karetki return/wysuw wiersza. Przykładowe dane wyjściowe tylko drukuje wyniki wyszukiwania jako pojedynczy ciąg.  
  
> [!NOTE]
>  Wynik stanu jest wszystko bezpośrednio po "..." do końca wiersza.  
  
```cpp  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\symbols\user32.pdb... Nie można odnaleźć pliku.**  
**c:\winnt\symbols\user32.pdb... Wersja jest niezgodna.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Załadowano symbole.**   
## <a name="see-also"></a>Zobacz też  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)