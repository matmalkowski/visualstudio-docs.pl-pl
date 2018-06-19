---
title: Za pomocą programu Visual Studio zestawy międzyoperacyjne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca0ff9a75d72bc723b767a43f12123094a520644
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146822"
---
# <a name="using-visual-studio-interop-assemblies"></a>Za pomocą programu Visual Studio zestawy międzyoperacyjne
Visual Studio zestawy międzyoperacyjne Zezwalaj zarządzanym aplikacjom dostęp do interfejsów modelu COM, które zapewni możliwość rozszerzenia programu Visual Studio. Istnieją pewne różnice między proste interfejsy COM i ich wersje międzyoperacyjnego. Na przykład wyników HRESULT zazwyczaj są reprezentowane jako wartości int i muszą być obsługiwani w taki sam sposób jak wyjątki, a parametry (szczególnie parametrów out) są traktowane inaczej.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Obsługa wyników HRESULT zwrócony do kodu zarządzanego z modelu COM  
 Interfejs COM jest wywoływana z kodu zarządzanego, sprawdź wartość HRESULT i Zgłoś wyjątek, jeśli jest to wymagane. <xref:Microsoft.VisualStudio.ErrorHandler> Klasa zawiera <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> przekazywania metodę, która zgłasza wyjątek modelu COM., w zależności od wartości HRESULT.  
  
 Domyślnie <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> zgłasza wyjątek, gdy są przekazywane HRESULT, która ma wartość mniejszą niż zero. W przypadku, gdy taki wyników HRESULT są dopuszczalne wartości i nie powinien być wyjątek, wartości dodatkowych wyników HRESULT powinny zostać przekazane do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po sprawdzane są wartości. Jeśli HRESULT testowane odpowiada wartości HRESULT jawnie przekazany do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, nie jest wyjątek.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Klasa zawiera stałe dla typowych wyników HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.S_OK> i <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wyników HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> i <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> dostępne są także <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> i <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metody, które odpowiadają makra zakończyło się pomyślnie, a w modelu COM.  
  
 Na przykład, należy wziąć pod uwagę następujące wywołanie funkcji, w którym <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> jest mniejsza od zera reprezentuje błąd dopuszczalne wartości zwracanej, ale inne HRESULT.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Jeśli istnieje więcej niż jeden dopuszczalne wartości zwracanych, dodatkowe wartości HRESULT właśnie można dołączyć do listy w wywołaniu <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Zwracanie wyników HRESULT dla modelu COM z kodu zarządzanego  
 Jeśli wystąpi żaden wyjątek, zwraca kod zarządzany <xref:Microsoft.VisualStudio.VSConstants.S_OK> funkcji COM, które ją. Usługa międzyoperacyjna modelu COM obsługuje typowe wyjątki, które są silnie typizowane w kodzie zarządzanym. Na przykład metodę, która odbiera niedopuszczalne `null` zgłasza argument <xref:System.ArgumentNullException>.  
  
 Jeśli nie jesteś niektórych wyjątków ma zostać zgłoszony, ale wiesz HRESULT chcesz powrócić do modelu COM, można użyć <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodę, aby zgłosić wyjątek, odpowiednie. Dzieje się tak nawet w przypadku błędów niestandardowych, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> próbuje zamapować HRESULT przekazywania do silnie typizowanego wyjątku. Jeśli nie, zgłasza wyjątek ogólny COM zamiast tego. Ultimate wynik jest, że HRESULT są przekazywane do <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> z kodu zarządzanego jest zwracana do funkcji modelu COM, która ją.  
  
> [!NOTE]
>  Wyjątki wpłynąć na wydajność i są przeznaczone do wskazywania niewłaściwym warunków. Warunki, które często występują powinien być obsługiwany w tekście, zamiast zwrócony wyjątek.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametry przekazywane jako typ void **  
 Wyszukaj [out] Parametry, które są zdefiniowane jako typ `void **` w modelu COM interfejsu, ale są zdefiniowane jako `[``iid_is``]` w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypu metody zestawu międzyoperacyjnego.  
  
 Czasami generuje interfejsu COM `IUnknown` obiektu i interfejsu COM następnie przekazuje ją jako typ `void **`. Te interfejsy są szczególnie istotne, ponieważ jeśli zmienna jest zdefiniowana jako [out] IDL, a następnie `IUnknown` obiekt jest liczony odwołanie z `AddRef` — metoda. Jeśli obiekt nie jest obsługiwana prawidłowo występuje przeciek pamięci.  
  
> [!NOTE]
>  `IUnknown` Obiekt utworzony przez interfejs COM i zwracany w zmiennej [out] powoduje przeciek pamięci, jeśli nie jest jawnie zwolnione.  
  
 Metody zarządzanych, obsługujące takie obiekty powinny traktować <xref:System.IntPtr> jako wskaźnik do `IUnknown` obiektu i wywołać <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodę, aby uzyskać obiekt. Obiekt wywołujący powinien następnie rzutowania wartości zwracanej do dowolnego typu, jest odpowiednie. Gdy obiekt nie jest potrzebna, należy wywołać <xref:System.Runtime.InteropServices.Marshal.Release%2A> do jego zwolnienia.  
  
 Poniżej przedstawiono przykładowy wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metody i obsługi `IUnknown` obiekt prawidłowo:  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  Następujące metody są znane do przekazania `IUnknown` obiekt wskaźniki jako typ <xref:System.IntPtr>. Ich obsługę zgodnie z opisem w tej sekcji.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>Opcjonalne [parametry out]  
 Wyszukaj parametrów, które są zdefiniowane jako [out] — Typ danych (`int`, `object`i tak dalej) w modelu COM interfejsu, ale są zdefiniowane jako tablic typu danych w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypu metody zestawu międzyoperacyjnego.  
  
 Niektóre COM interfejsy, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, Traktuj [opcjonalne parametry out]. Jeśli obiekt nie jest wymagane, zwróć te interfejsy COM `null` wskaźnika jako wartość tego parametru zamiast tworzenia obiektu [out]. To jest celowe. Dla tych interfejsów `null` wskaźniki będą traktowani jako część prawidłowe działanie pakiet VSPackage, a błąd nie występuje.  
  
 Ponieważ środowisko CLR nie zezwala na wartość parametrem [out] jako `null`, część zaprojektowane zachowanie tych interfejsów nie jest dostępna w kodzie zarządzanym. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Metody zestawu międzyoperacyjnego dla odpowiednich interfejsów obejść ten problem, definiując odpowiednich parametrów jako tablice, ponieważ środowisko CLR zezwala na przekazywanie `null` tablic.  
  
 Zarządzane implementacje metody te należy umieścić `null` tablicy do parametru, gdy nie ma nic do zwrócenia. W przeciwnym razie utwórz tablicą jednego elementu poprawnego typu i umieścić w tablicy wartości zwracanej.  
  
 Zarządzane metody, które otrzymywanie informacji z interfejsów z opcjonalne [out] Parametry pobierają parametr w postaci tablicy. Po prostu zbadać wartość pierwszego elementu tablicy. Jeśli nie jest `null`, Traktuj pierwszego elementu, tak jakby był on pierwotny parametr.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Przekazywanie stałych w parametrach wskaźnika  
 Wyszukaj parametry, które zostały zdefiniowane jako [in] wskaźniki interfejsu COM, ale które są zdefiniowane jako <xref:System.IntPtr> wpisz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypu metody zestawu międzyoperacyjnego.  
  
 Podobne problem występuje, gdy interfejs COM przekazuje wartość specjalnych, takich jak 0, -1 lub -2, a nie wskaźnik do obiektu. W odróżnieniu od [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], CLR nie zezwala na stałe można rzutować jako obiekty. Zamiast tego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu międzyoperacyjnego definiuje jako parametr <xref:System.IntPtr> typu.  
  
 Zarządzane implementacje metod powinny wykorzystywać fakt, że <xref:System.IntPtr> klasa ma zarówno atrybut `int` i `void *` konstruktorów, aby utworzyć <xref:System.IntPtr> z obiektem lub stała liczba całkowita w odpowiednich przypadkach.  
  
 Zarządzane metod, które odbierają <xref:System.IntPtr> parametry tego typu należy używać <xref:System.IntPtr> wpisz operatory konwersji do obsługi wyniki. Najpierw przekonwertuj <xref:System.IntPtr> do `int` i przetestowania stałe całkowite istotne. Jeśli wartości nie są zgodne, przekonwertuj go wymaganego typu obiektu i kontynuować.  
  
 Przykłady to znaleźć <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE zwracać wartości przekazane jako [parametry out]  
 Wyszukaj metod, które mają `retval` wartości zwracanej w interfejsie COM, ale ma `int` zwracać wartości i dodatkowy [parametr tablicy w out] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypu metody zestawu międzyoperacyjnego. Powinno być jasne, czy te metody wymagają specjalnej obsługi, ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypy metody zestawu międzyoperacyjnego mieć jeden parametr więcej niż metody interfejsu COM.  
  
 Liczba interfejsów modelu COM, które zajmują się działanie OLE wysyłane informacje o stanie OLE program wywołujący przechowywane w `retval` zwrócić wartość interfejs. Zamiast wartości zwracanej odpowiadającego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metody zestawu międzyoperacyjnego wysłać informacje o powrót do wywoływania programu przechowywane w [out] parametr tablicy.  
  
 Zarządzane implementacje metod należy utworzyć macierz jeden element tego samego typu jako parametr [out] i umieść je w parametrze. Wartość elementu tablicy powinna być taka sama jak odpowiednie COM `retval`.  
  
 Zarządzane metody, które wywołują interfejsy tego typu należy pobierać pierwszego elementu z tablicy [out]. Ten element może być traktowana tak, jakby była `retval` wartość zwracana z odpowiedniego interfejsu COM.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)