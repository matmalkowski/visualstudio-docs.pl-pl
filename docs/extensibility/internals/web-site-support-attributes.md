---
title: Witryna sieci Web pomocy technicznej atrybuty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b312322c1d707f13c5121f1fd159f3fd7736886c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="web-site-support-attributes"></a>Witryna sieci Web pomocy technicznej atrybutów
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt witryny sieci Web może zostać rozszerzony do zapewniają obsługę sieci Web języków programowania. Język musi się zarejestrować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, aby szablony projektu może występować w **nowej witryny sieci Web** okno dialogowe, gdy jest wybrany język.

Przykład IronPython Studio obsługuje witryny sieci web. Próbka zawiera następujące klasy atrybutu zarejestrować IronPython jako język plik codebehind dla nowych projektów sieci Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Ten atrybut jest umieszczany w projekcie języka. Dodaje język do listy języków programowania w sieci Web **języka** na liście **nowej witryny sieci Web** okno dialogowe. Na przykład następujący kod dodaje IronPython do listy:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Ten atrybut określa również ścieżkę szablony, aby wskazywała na folder szablonów. Aby uzyskać więcej informacji o lokalizacji folderu Szablony, zobacz [szablony witryn sieci Web pomocy technicznej](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Ten atrybut jest umieszczany w projekcie języka. Umożliwia projekt witryny sieci Web zagnieździć jeden typ pliku (dotyczących) w obszarze innego typu pliku (podstawowy) w **Eksploratora rozwiązań**.

 Na przykład następujący kod określa, że plik został IronPython jest powiązany z plikiem aspx. Po utworzeniu nowej strony sieci Web .aspx w rozwiązaniu witryny sieci IronPython Web plik źródłowy PY i jest generowany i będzie wyświetlany jako węzeł podrzędny strony .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Ten atrybut jest umieszczona na pakiet projektu języka. Jest ona wybierana dostawcy IntelliSense dla języka.

 Na przykład następujący kod określa, że wystąpienie PythonIntellisenseProvider, która implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, powinny być tworzone na żądanie do świadczenia usług języka.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementacja IVsIntellisenseProject obsługuje odwołania i wywołuje kompilatora języka, gdy strony sieci Web z kodu jest wymagane, ale nie są buforowane.

## <a name="see-also"></a>Zobacz też
 [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)