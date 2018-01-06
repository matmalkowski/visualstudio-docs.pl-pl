---
title: Projekt modelowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31c3d87a44838ead7663ff4c156985ab1b8e98eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="project-modeling"></a>Projekt modelowania
Następnym krokiem w zapewnianiu automatyzacji dla projektu jest zaimplementowanie obiektów standardowe projektu: <xref:EnvDTE.Projects> i `ProjectItems` kolekcje; `Project` i <xref:EnvDTE.ProjectItem> obiekty; a pozostałe obiekty unikatowe dla implementacji. Te standardowe obiekty są zdefiniowane w pliku Dteinternal.h. Implementacja standardowych obiektów znajduje się w przykładowej BscPrj. Te klasy jako modele służy do tworzenia własnego projektu standardowych obiektów, które autonomiczna side-by-side z obiektami projektu z innych typów projektów.  
  
 Konsumenta automatyzacji przyjęto założenie, aby można było wywołać <xref:EnvDTE.Solution>("`<UniqueProjName>")` i <xref:EnvDTE.ProjectItems> (`n`) gdzie n to numer indeksu dla uzyskania określonego projektu w rozwiązaniu. Tego wywołania automatyzacji powoduje, że środowisko do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> na odpowiedni projekt hierarchii, przekazując VSITEMID_ROOT jako parametr ItemID i VSHPROPID_ExtObject jako parametr VSHPROPID. `IVsHierarchy::GetProperty`Zwraca `IDispatch` wskaźnik do obiektu automatyzacji, podając podstawowe `Project` interfejs, który został zaimplementowany.  
  
 Poniżej przedstawiono składnię `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT``*pvar`  
  
 `);`  
  
 Projekty uwzględnić zagnieżdżanie i tworzenia grup elementów projektu za pomocą kolekcji. Hierarchia wygląda następująco.  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Zagnieżdżanie oznacza, że <xref:EnvDTE.ProjectItem> obiekt może być <xref:EnvDTE.ProjectItems> kolekcji, w tym samym czasie ponieważ `ProjectItems` kolekcji może zawierać zagnieżdżone obiekty. Przykładowy projekt podstawowe nie pokazują tego zagnieżdżenia. Zaimplementowanie `Project` obiekt uczestniczyć w strukturze drzewa, która charakteryzuje projekt ogólny model automatyzacji.  
  
 Automatyzacja projektu następuje ścieżki na poniższym diagramie.  
  
 ![Obiekty projektu programu Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automatyzacja projektu  
  
 Jeśli nie implementują `Project` obiekt środowiska nadal będzie zwracać ogólnego `Project` obiekt, który zawiera tylko nazwę projektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>