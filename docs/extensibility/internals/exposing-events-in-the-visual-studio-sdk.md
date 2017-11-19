---
title: "Udostępnianie zdarzenia w programie Visual Studio SDK | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7b392ac841a50d835186e79a383e404e7fba190
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Udostępnianie zdarzenia w programie Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Umożliwia źródła zdarzeń przy użyciu automatyzacji. Zaleca się, że źródła zdarzeń dla projektów i elementów projektu.  
  
 Zdarzenia są pobierane przez klientów automatyzacji z <xref:EnvDTE.DTEClass.Events%2A> obiektu lub <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). Wywołania środowiska `IDispatch::Invoke` za pomocą `DISPATCH_METHOD` lub `DISPATCH_PROPERTYGET` flagi do zwrócenia zdarzenia.  
  
 Następujący proces wyjaśniono, jak zdarzenia specyficzne dla pakiet VSPackage są zwracane.  
  
1.  Uruchamia środowisko.  
  
2.  Odczytuje z rejestru wszystkie nazwy wartości w automatyzacji, AutomationEvents i AutomationProperties kluczach wszystkie pakiety VSPackage i przechowuje te nazwy w tabeli.  
  
3.  Wywołuje konsumenta automatyzacji, w tym przykładzie `DTE.Events.AutomationProjectsEvents` lub `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  Środowisko wyszukuje parametr ciągu w tabeli i ładuje odpowiedni pakiet VSPackage.  
  
5.  Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody przy użyciu nazwy przekazywany w wywołaniu; w tym przykładzie AutomationProjectsEvents lub AutomationProjectItemsEvents.  
  
6.  Pakiet VSPackage tworzy obiekt główny, który ma metody, na przykład `get_AutomationProjectsEvents` i `get_AutomationProjectItemEvents` , a następnie zwraca IDispatch wskaźnik do obiektu.  
  
7.  Środowisko wywołuje odpowiedniej metody, na podstawie nazwy przekazany do wywołania automatyzacji.  
  
8.  `get_` Metoda tworzy inny obiekt zdarzenia na podstawie IDispatch, który implementuje zarówno `IConnectionPointContainer` interfejsu i `IConnectionPoint` interfejsu i zwraca IDispatchpointer do obiektu.  
  
 Do udostępnienia zdarzenia przy użyciu automatyzacji, musi odpowiadać na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> i obserwowanie ciągów, które można dodać do rejestru. W przykładowym podstawowego projektu ciągi są "BscProjectsEvents" i "BscProjectItemsEvents".  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Wpisy rejestru z próbki podstawowego projektu  
 W tej sekcji przedstawiono dodania wartości zdarzenia automatyzacji do rejestru.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 "AutomationProjectEvents"="zwraca obiekt AutomationProjectEvents"  
  
 "AutomationProjectItemEvents"="zwraca obiekt AutomationProjectItemsEvents"  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|Domyślne (@)|REG_SZ|Nieużywane|Nieużywane. W polu danych służy do dokumentacji.|  
|AutomationProjectsEvents|REG_SZ|Nazwa obiektu zdarzenia.|Nazwa klucza jest ważna. W polu danych służy do dokumentacji.<br /><br /> W tym przykładzie pochodzą z przykładowych podstawowego projektu.|  
|AutomationProjectItemEvents|REG_SZ|Nazwa obiektu zdarzeń|Nazwa klucza jest ważna. W polu danych służy do dokumentacji.<br /><br /> W tym przykładzie pochodzą z przykładowych podstawowego projektu.|  
  
 Gdy żądane są dowolne obiekty zdarzeń przez konsumenta automatyzacji, Utwórz obiekt główny, który ma metody dla dowolnego zdarzenia, które obsługuje VSPackage. Środowisko wywołuje odpowiednie `get_` metody dla tego obiektu. Na przykład jeśli `DTE.Events.AutomationProjectsEvents` jest nazywany `get_AutomationProjectsEvents` wywołania metody do obiektu głównego.  
  
 ![Zdarzenia projektu programu Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Model automatyzacji dla zdarzenia  
  
 Klasa `CProjectEventsContainer` reprezentuje obiekt źródłowy dla BscProjectsEvents, podczas gdy `CProjectItemsEventsContainer` reprezentuje obiekt źródłowy dla BscProjectItemsEvents.  
  
 W większości przypadków musi zwracać nowy obiekt dla każdego żądania zdarzenia, ponieważ większość obiektów zdarzeń obiektu filtra. Gdy wyzwalać zdarzenie, Sprawdź ten filtr, aby sprawdzić, czy program obsługi zdarzeń jest wywoływana.  
  
 AutomationEvents.h i AutomationEvents.cpp znajdują się deklaracje i implementacji klasy w poniższej tabeli.  
  
|Class|Opis|  
|-----------|-----------------|  
|`CAutomationEvents`|Implementuje obiekt główny zdarzenia pobierane z `DTE.Events` obiektu.|  
|`CProjectsEventsContainer`i`CProjectItemsEventsContainer`|Implementuje obiekty źródła zdarzeń, które wyzwalać odpowiednie zdarzenia.|  
  
 Poniższy przykład kodu pokazuje, jak odpowiedzieć na żądanie dla obiekt zdarzenia.  
  
```cpp  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 W powyższym kodzie `g_wszAutomationProjects` to nazwa kolekcji projektów ("FigProjects"), `g_wszAutomationProjectsEvents` ("FigProjectsEvents") i `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") są nazwy zdarzenia projektu i projektu elementy zdarzenia, które pochodzą z sieci Implementacja pakiet VSPackage.  
  
 Obiekty zdarzeń są pobierane z tej samej lokalizacji centralnej `DTE.Events` obiektu. Dzięki temu wszystkie obiekty zdarzeń są grupowane tak, aby użytkownik końcowy nie musi przejść całego obiektu model można znaleźć określonego zdarzenia. Umożliwia to także podać konkretne obiekty pakiet VSPackage, zamiast konieczności wykonania kodu dla zdarzenia systemowe. Jednak dla użytkownika końcowego, który musi znaleźć zdarzenie dla Twojego `ProjectItem` interfejsu, nie jest od razu jasne, z której są pobierane ten obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Przykłady VSSDK](http://aka.ms/vs2015sdksamples)