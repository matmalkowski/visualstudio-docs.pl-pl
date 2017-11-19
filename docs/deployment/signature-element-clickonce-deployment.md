---
title: "&lt;Podpis&gt; elementu (wdrażania ClickOnce) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords: <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: a60156c77dfc33475d3913c3fed2e30159f03959
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Podpis&gt; elementu (wdrażania ClickOnce)
Zawiera informacje potrzebne do cyfrowego podpisywania manifestu tego wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Uwagi  
 Podpisywanie manifestu wdrożenia przy użyciu podpisu koperty jest opcjonalne, ale zalecane. Aby uzyskać więcej informacji na temat podpisywania XML plików Zobacz sieci World Wide Web konsorcjum zalecenia, "Podpis XML składni i przetwarzanie" w sposób opisany w [http://www.w3.org/TR/xmldsig-core/](http://www.w3.org/TR/xmldsig-core/).  
  
 Jeśli chcesz zarejestrować w manifeście, należy podać wartości skrótu dla wszystkich plików. Nie można podpisać manifest z plikami, które nie jest przemieszane, ponieważ użytkownicy nie może zweryfikować zawartości bez haszowania plików.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `Signature` elementu w manifeście wdrażania, używane w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)