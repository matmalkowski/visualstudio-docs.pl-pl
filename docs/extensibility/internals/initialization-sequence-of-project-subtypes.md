---
title: Sekwencja inicjowania podtypów projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe7e7a574d04ec9a49252e32e0fbb8b5685778aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131616"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sekwencja inicjowania podtypów projektu
Środowisko tworzy projekt wywołując projektu Podstawowa implementacja fabryki <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Konstrukcja podtypu projektu rozpoczyna się, gdy środowisko określa, czy listy identyfikatorów GUID typu projektu dla rozszerzenia pliku projektu nie jest pusta. Rozszerzenie pliku projektu i identyfikator GUID projektu Określ, czy projekt jest [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] typu projektu. Na przykład rozszerzenie vbproj i {F184B08F-C81C-45F6-A57F-5ABD9991F28F} zidentyfikować [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu.

## <a name="environments-initialization-of-project-subtypes"></a>Inicjowanie środowiska podtypów projektu
 Poniższa procedura zawiera szczegóły dotyczące sekwencji inicjowania systemu projektu w wielu podtypów projektu.

1.  Środowisko wywołuje podstawowego projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, a podczas jego plik projektu analizuje projektu odnajduje nie jest typem projektu agregacji listy identyfikatorów GUID `null`. Projekt zaprzestaje bezpośrednio tworzenie jego projektu.

2.  Wywołania projektu `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> usługi można utworzyć podtypu projektu przy użyciu wdrożenia w środowisku <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody. W ramach tej metody środowiska sprawia, że wywołania funkcji rekursywnych do Twojej implementacje <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> identyfikatorów GUID, począwszy od podtypu projektu najbardziej zewnętrznego typu metody, gdy jest przejście na liście projektu.

     Następujące szczegóły kroków inicjowania.

    1.  Wdrożenia w środowisku <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> wywołania metody `HrCreateInnerProj` metody z deklaracją następujących funkcji:

         <CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Gdy ta funkcja jest wywoływana po raz pierwszy, oznacza to, że dla podtypu projektu najbardziej zewnętrznego parametry `pOuter` i `pOwner` są przekazywane w jako `null` i funkcja ustawia podtyp projektu najbardziej zewnętrznego `IUnknown` do `pOuter`.

    2.  Środowisko wywołuje `HrCreateInnerProj` funkcji z drugiego identyfikator GUID typu projektu na liście. Ten identyfikator GUID odpowiada drugi podtypu projektu wewnętrzny wykonywanie krok po kroku kierunku podstawowego projektu w sekwencji agregacji.

    3.  `pOuter` Teraz wskazuje `IUnknown` podtypu projektu najbardziej zewnętrznego i `HrCreateInnerProj` Twojego wdrożenia wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> następuje wywołanie implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metoda przekazywania kontrolowania `IUnknown` podtypu projektu najbardziej zewnętrznego `pOuter`. Należących do projektu (podtyp projektu wewnętrzny) musi tworzenia własnego obiektu projektu agregacji. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> przekazać we wskaźniku do implementacji metody `IUnknown` wewnętrzny projektu, która jest agregowana. Te dwie metody tworzenia obiektu agregacji i implementacjach użytkownika należy wykonywać reguły agregacji COM, aby upewnić się, że podtypu projektu nie przechodzili zawierający liczba odwołań do samej siebie.

    4.  `HrCreateInnerProj` wywołania implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. W przypadku tej metody podtypu projektu działa jego inicjowania. Można na przykład zarejestrować zdarzenia rozwiązania w <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5.  `HrCreateInnerProj` jest wywoływany rekursywnie, aż do osiągnięcia ostatniego identyfikatora GUID (podstawowy projekt) na liście. Dla każdego z tych wywołań kroki c do d, są powtarzane. `pOuter` wskazuje podtyp projektu najbardziej zewnętrznego `IUnknown` dla każdego poziomu agregacji.

## <a name="example"></a>Przykład

W poniższym przykładzie opisano proces programowe w przybliżonej reprezentację <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody, w jakiej jest implementowany przez środowisko. Kod jest tylko przykładowe; nie jest on przeznaczony do kompilacji, a wszystkie sprawdzanie błędów został usunięty z myślą o przejrzystości.

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)