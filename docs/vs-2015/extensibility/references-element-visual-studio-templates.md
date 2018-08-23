---
title: Odwołuje się Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54ff9d03291adf55f0bae3d4cb85d5f8c075b431
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680616"
---
# <a name="references-element-visual-studio-templates"></a>Odwołania — element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [odwołania — Element (szablony Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/references-element-visual-studio-templates).  
  
Grupuje odwołania do zestawów, które szablon dodaje się do projektów.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Odwołania >  
  
## <a name="syntax"></a>Składnia  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Dokumentacja](../extensibility/reference-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa odwołanie do zestawu do dodania, gdy element zostanie dodany do projektu. Musi istnieć co najmniej jeden `Reference` elementów w `References` elementu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|  
  
## <a name="remarks"></a>Uwagi  
 `References` jest podrzędnym elementem opcjonalnym elementu `TemplateContent`.  
  
 `Reference` i `References` elementów należy używać tylko w plikach .vstemplate, które mają `Type` wartość atrybutu `Item`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `TemplateContent` element szablon elementu. Poniższy kod XML dodaje odwołania do zestawów: System.dll i System.Data.dll.  
  
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

