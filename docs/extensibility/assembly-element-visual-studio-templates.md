---
title: "Assembly — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5202d7468ecefe9de1754f592eef826f0390b869
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly — Element (szablony Visual Studio)
Określa informacje o zestawie używane w szablonie, aby dodać odwołanie do tego zestawu do projektów.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Odwołania >  
 \<Odwołania >  
 \<Zestaw >  
  
## <a name="syntax"></a>Składnia  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Dokumentacja](../extensibility/reference-element-visual-studio-templates.md)|Określa odwołanie do zestawu, aby dodać, gdy element zostanie dodany do projektu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Ten tekst Określa zestaw do dodania do projektu podczas tworzenia wystąpienia klasy szablonu elementu. Ta nazwa zestawu musi być określona w jednym z następujących sposobów:  
  
-   Jako pełną nazwą zestawu. Na przykład:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Jako zwykły tekst odwołanie. Na przykład:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Uwagi  
 `Assembly`jest elementem podrzędnym wymagane `Reference`.  
  
 `Reference`, `References,` i `Assembly` elementów można używać tylko w plikach .vstemplate `Type` wartość atrybutu `Item`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia `TemplateContent` element szablonu elementu. Plik XML dodaje odwołania do zestawów System.dll i System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)