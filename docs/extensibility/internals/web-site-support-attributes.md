---
title: Witryna sieci Web pomocy technicznej atrybuty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 868fe0785c90a174610b9fff837fc6fbfb084e83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support-attributes"></a>Witryna sieci Web pomocy technicznej atrybutów
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Projekt witryny sieci Web może zostać rozszerzony do zapewniają obsługę sieci Web języków programowania. Język musi się zarejestrować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, aby szablony projektu może występować w **nowej witryny sieci Web** okno dialogowe, gdy jest wybrany język.  
  
 Przykład IronPython Studio obsługuje witryny sieci web. Obejmuje on następujące klasy atrybutu zarejestrować IronPython jako język plik codebehind dla nowych projektów sieci Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Ten atrybut jest umieszczany w projekcie języka. Dodaje język do listy języków programowania w sieci Web **języka** na liście **nowej witryny sieci Web** okno dialogowe. Dodaje na przykład następujące IronPython do listy:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Ten atrybut określa również ścieżkę szablony, aby wskazywała na folder szablonów. Aby uzyskać więcej informacji o lokalizacji folderu Szablony, zobacz [szablony witryn sieci Web pomocy technicznej](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Ten atrybut jest umieszczany w projekcie języka. Umożliwia projekt witryny sieci Web zagnieździć jeden typ pliku (dotyczących) w obszarze innego typu pliku (podstawowy) w **Eksploratora rozwiązań**.  
  
 Na przykład:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Określa, że plik został IronPython jest powiązany z plikiem aspx. Po utworzeniu nowej strony sieci Web .aspx w rozwiązaniu witryny sieci IronPython Web plik źródłowy PY i jest generowany i będzie wyświetlany jako węzeł podrzędny strony .aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Ten atrybut jest umieszczona na pakiet projektu języka. Jest ona wybierana dostawcy Intellisense dla języka.  
  
 Na przykład:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Określa, że wystąpienie PythonIntellisenseProvider, która implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, powinny być tworzone na żądanie do świadczenia usług języka.  
  
 Implementacja IVsIntellisenseProject obsługuje odwołania i wywołuje kompilatora języka, gdy strony sieci Web z kodu jest wymagane, ale nie są buforowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)