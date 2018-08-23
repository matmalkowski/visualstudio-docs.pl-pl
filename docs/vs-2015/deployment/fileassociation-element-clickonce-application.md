---
title: '&lt;fileassociation —&gt; — Element (aplikacja ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 3a3589387b00eb1ade9c9b60b0845bc2421b3486
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633212"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileassociation —&gt; — Element (aplikacja ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ &lt;fileassociation —&gt; — Element (aplikacja ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/fileassociation-element-clickonce-application).  
  
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
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `fileAssociation` Element jest opcjonalne. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`extension`|Wymagane. Rozszerzenie pliku, który ma zostać skojarzony z aplikacją.|  
|`description`|Wymagane. Opis typu plików do użytku przez powłokę.|  
|`progid`|Wymagane. Nazwa, który unikatowo identyfikuje typ pliku.|  
|`defaultIcon`|Wymagane. Określa ikonę do używania z plików z tego rozszerzenia. Plik ikony musi być określona za pomocą [ \<Plik > Element](../deployment/file-element-clickonce-application.md) w ramach [ \<zestawu > Element](../deployment/assembly-element-clickonce-application.md) zawierający ten element.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element musi zawierać odwołanie do przestrzeni nazw XML "urn: schemas-microsoft-com:clickonce.v1". Jeśli `<fileAssociation>` element jest używany, musi być późniejsza `<application>` elementu w jego element nadrzędny [ \<zestawu > Element](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nie spowoduje zastąpienie istniejących skojarzeń plików. Aplikacja ClickOnce może jednak zmienić rozszerzenie pliku dla bieżącego użytkownika. Po odinstalowaniu tej aplikacji ClickOnce ClickOnce spowoduje usunięcie skojarzenia pliku dla użytkownika, a następnie ponownie skojarzenia komputera jest aktywny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano `fileAssociation` elementów w aplikacji manifestu dla aplikacji edytora tekstu, wdrożone za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Ten przykładowy kod zawiera również [ \<Plik > Element](../deployment/file-element-clickonce-application.md) wymagane przez `defaultIcon` atrybutu.  
  
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



