---
title: 'Porady: pomijanie powiadomienia o zmianie pliku | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 209006129bcb2cfaaf88233768df1d9597cd09a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-file-change-notifications"></a>Porady: pomijanie powiadomienia o zmianie pliku
Po zmianie pliku fizycznego reprezentująca bufor tekstowy, zostanie wyświetlone okno dialogowe z komunikatem **czy chcesz zapisać zmiany w następujących elementach?** Jest to nazywane powiadomienia o zmianie pliku. Jeśli wiele zmian mają być do pliku, jednak to okno dialogowe Wyświetlanie wielokrotnie może szybko stać się irytujące.  
  
 To okno dialogowe przy użyciu poniższej procedury można pominąć programowo. Dzięki temu możesz ponownie załadować plik natychmiast bez konieczności Monituj użytkownika, aby zapisać zmiany w każdym.  
  
### <a name="to-suppress-file-change-notification"></a>Aby wyłączyć powiadomienia o zmianie pliku  
  
1.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodę, aby określić obiekt buforu tekstu, który jest skojarzony z Otwórz plik.  
  
2.  Bezpośrednie <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiekt, który jest w pamięci, aby zignorować monitorowania zmian w pliku, uzyskując <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interfejsu z <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu (dane dokumentu), a następnie wykonania <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metody z `fIgnore` parametru Ustaw `true`.  
  
3.  Wywołanie metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsów można zaktualizować w pamięci <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu o zmiany pliku (na przykład po dodaniu pola do składnika).  
  
4.  Zaktualizuj plik na dysku ze zmianami, bez uwzględniania wszelkie oczekujące zmiany, które użytkownik może być w toku.  
  
     W ten sposób można kierować <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> powiadomienia o zmianie obiektu można wznowić monitorowania dla plików, zmiany, które są generowane, a także wszystkie oczekujące edycje odzwierciedla buforu tekstu w pamięci. Plik na dysku odzwierciedla najnowszej kod wygenerowany przez Ciebie i wszelkie wcześniej zapisano zmiany przez użytkownika w kodzie edytować użytkownika.  
  
5.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodę, aby powiadomić <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu można wznowić monitorowania pliku powiadomienia o zmianach, ustawiając `fIgnore` parametr `false`.  
  
6.  Jeśli zamierzasz wprowadzić kilka zmian pliku, tak jak w przypadku kontroli kodu źródłowego (SCC), należy wskazać usługi o zmianie pliku globalnego tymczasowo zawiesić powiadomienia o zmianie pliku.  
  
     Na przykład w przypadku ponownego zapisywania pliku i następnie zmiany sygnatury czasowej, musi wstrzymaniu powiadomienia o zmianie pliku jako operacji ponownego zapisywania i timestample, każdy traktowane jako zdarzenie zmiany oddzielny plik. Aby włączyć powiadomienia o zmianie pliku globalnego należy zamiast tego wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniżej pokazano, jak wyłączyć powiadomienia o zmianie pliku.  
  
```cpp  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli tej sprawy obejmuje wiele zmian do pliku, tak jak w przypadku SCC, następnie należy wznowić powiadomienia o zmianie pliku globalnego przed wysłaniem alertu dane dokumentu można wznowić monitorowania dla zmian plików.