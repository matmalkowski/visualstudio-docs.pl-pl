---
title: '&lt;fileAssociation&gt; elementu (aplikacji ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: bd5d7ed1a37923cefc4a6b7975610b6016fd0ae6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; elementu (aplikacji ClickOnce)
Określa rozszerzenie pliku do skojarzenia z aplikacją.  
  
## <a name="syntax"></a>Składnia  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `fileAssociation` Element jest opcjonalny. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`extension`|Wymagany. Rozszerzenie pliku, który ma zostać skojarzony z aplikacją.|  
|`description`|Wymagany. Opis typów plików do użytku przez powłokę.|  
|`progid`|Wymagany. Nazwa, który unikatowo identyfikuje typ pliku.|  
|`defaultIcon`|Wymagany. Określa ikonę do używania plików dla tego rozszerzenia. Plik ikony musi być określona za pomocą [ \<pliku > Element](../deployment/file-element-clickonce-application.md) w [ \<zestawu > Element](../deployment/assembly-element-clickonce-application.md) zawierający ten element.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element musi zawierać odwołanie do przestrzeni nazw XML "urn: schemas-microsoft-com:clickonce.v1". Jeśli `<fileAssociation>` element jest używany, musi występować po `<application>` elementu nadrzędnego [ \<zestawu > elementu](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]nie spowoduje zastąpienie istniejącego skojarzenia plików. Jednak aplikacji ClickOnce, mogą zastąpić rozszerzenie pliku dla bieżącego użytkownika. Po odinstalowaniu tej aplikacji ClickOnce ClickOnce usuwa skojarzenie pliku dla użytkownika i skojarzenie dla poszczególnych komputerów active ponownie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `fileAssociation` elementów w aplikacji manifestu dla aplikacji edytora tekstu, wdrożenie za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Ten przykładowy kod zawiera również [ \<pliku > Element](../deployment/file-element-clickonce-application.md) wymagane przez `defaultIcon` atrybutu.  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)