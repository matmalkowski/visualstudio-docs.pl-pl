---
title: Odwołania — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9e0217360b2a8e9c6c8e723561aff383ed3226d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="reference-element-visual-studio-templates"></a>Reference — Element (szablony Visual Studio)
Określa odwołanie do zestawu, aby dodać, gdy element zostanie dodany do projektu.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Odwołania >  
 \<Odwołania >  
  
## <a name="syntax"></a>Składnia  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa informacje o zestawie używane w szablonie, aby dodać odwołanie do tego zestawu do projektów. Musi istnieć jedna `Assembly` element w każdym `Reference` elementu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Odwołania](../extensibility/references-element-visual-studio-templates.md)|Grupy odwołania do zestawów, które do szablonu dodawany do projektów.|  
  
## <a name="remarks"></a>Uwagi  
 `Reference` jest elementem podrzędnym wymagane `References`.  
  
 `Reference` i `References` elementów można używać tylko w plikach .vstemplate `Type` wartość atrybutu `Item`.  
  
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