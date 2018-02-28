---
title: "Implementacja interfejsów pomocnika inteligentnego hosta | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba571f6ad66855c44902e06467889e2cae5b4555
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implementacja interfejsów pomocnika inteligentnego hosta
[Interfejs IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md) interfejsu znacznie upraszcza zadanie tworzenia host inteligentny do aktywnego debugowania, ponieważ zapewnia implementacji dla wielu interfejsy niezbędne do obsługi inteligentne.  
  
 Jako hosta inteligentnego przy użyciu `IDebugDocumentHelper`, aplikację hosta należy wykonać tylko trzy czynności:  
  
1.  `CoCreate`Menedżer debugowania procesu i użyj [interfejs IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md) interfejsu, aby dodać aplikację do listy z możliwością debugowania aplikacji.  
  
2.  Utwórz obiekt pomocnika dokumentu debugowania dla każdego skryptu obiekt, za pomocą [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) metody. Upewnij się, są zdefiniowane nazwy dokumentu, dokument nadrzędny, tekst i blokach skryptu.  
  
3.  Implementowanie [interfejs IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md) obiektu implementującego interfejs [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu (co jest potrzebne do aktywnych skryptów). Tylko nieuproszczony metody na `IActiveScriptSiteDebug` interfejsu po prostu deleguje do elementu pomocniczego.  
  
 Opcjonalnie można zaimplementować hosta [interfejs IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) interfejsu wymaga dodatkową kontrolę nad kolor składni, tworzenie kontekstu dokumentu i inne funkcje rozszerzonej.  
  
 Główne ograniczenie pomocnika inteligentnego hosta jest, że dokumentów, których zawartość zmienić lub zmniejszyć rozmiar po zostały one dodane (mimo że dokumenty można rozwinąć) może obsługiwać tylko. W przypadku wielu hostów Inteligentne funkcje, które zapewnia jest jednak co jest potrzebne.  
  
 W poniższych sekcjach opisano każdy krok bardziej szczegółowo.  
  
## <a name="create-an-application-object"></a>Utwórz obiekt aplikacji  
 Przed użyciem pomocnika inteligentnego hosta, należy utworzyć [interfejs IDebugApplication](../winscript/reference/idebugapplication-interface.md) obiektu do reprezentowania aplikacji w debugerze.  
  
#### <a name="to-create-an-application-object"></a>Aby utworzyć obiekt aplikacji  
  
1.  Utwórz wystąpienie debugowania procesu za pomocą Menedżera `CoCreateInstance`.  
  
2.  Wywołanie [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Ustaw nazwę dla aplikacji za pomocą [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Dodaj obiekt aplikacji do listy z możliwością debugowania aplikacji przy użyciu [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Poniższy kod przedstawia proces, ale nie obejmuje sprawdzanie błędów lub innych technik programowania, niezawodne.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Przy użyciu IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Aby użyć pomocnika (minimalny sekwencja kroków)  
  
1.  Dla każdego dokumentu hosta, należy utworzyć przy użyciu Pomocnika [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Wywołanie [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) na pomocnika, podając nazwę, atrybuty dokumentu i tak dalej.  
  
3.  Wywołanie [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) z nadrzędnego pomocnika dla dokumentu (lub wartość NULL, jeśli dokument jest katalogiem głównym) do definiowania położenie dokumentu w drzewie i widoczny dla debugera.  
  
4.  Wywołanie [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) lub [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) do definiowania tekst dokumentu. (Te można wywoływać wielokrotnie Jeśli dokument zostanie pobrany przyrostowo, tak jak w przypadku przeglądarki.)  
  
5.  Wywołanie [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) Aby zdefiniować zakresów dla każdego bloku skryptu i aparatów skryptów skojarzone.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Implementowanie IActiveScriptSiteDebug  
 Aby zaimplementować [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), Pobierz pomocnika odpowiadający danej lokacji, a następnie zachęcić dokumentu początkowego przesunięcia kontekstu danego źródła w następujący sposób:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Następnie użyj pomocnika, aby utworzyć nowy kontekst dokumentu przesunięcia znaku:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Aby zaimplementować [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), po prostu Wywołaj `IDebugApplication::GetRootNode` (dziedziczone z [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 Aby zaimplementować [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), po prostu zwrot `IDebugApplication` początkowo utworzony za pomocą Menedżera debugowania procesu.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Opcjonalny interfejs IDebugDocumentHost  
 Host może zapewniać implementację elementu [interfejs IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) za pomocą [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) zapewniające dodatkową kontrolę nad pomocnika. Oto niektóre z kluczowych czynników, które interfejs hosta można wykonać:  
  
-   Dodawanie tekstu przy użyciu [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) tak, że host nie trzeba podać rzeczywiste znaki natychmiast. Gdy znaki są naprawdę potrzebne, wywoła Pomocnika [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) na hoście.  
  
-   Zastąpienie kolorowanie składni domyślne, dostarczone przez pomocnika. Wywołania Pomocnika [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) ustalenie kolorowanie zakresu znaków, nastąpi powrót na jej wykonanie domyślne, jeśli host zwraca `E_NOTIMPL`.  
  
-   Przewidują kontrolowanie nieznany kontekstach dokumentu utworzone przez pomocnika zaimplementowanie [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). Dzięki temu hosta do przesłonięcia funkcji Domyślna implementacja kontekstu dokumentu.  
  
-   Podaj nazwę ścieżki systemu plików dla dokumentu. Niektóre debugowania UI umożliwia zezwolić użytkownikowi na edytować i zapisać zmiany w dokumencie. [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) jest wywoływana w celu powiadomienia hosta po zapisaniu dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd debugowania aktywnego skryptu](../winscript/active-script-debugging-overview.md)