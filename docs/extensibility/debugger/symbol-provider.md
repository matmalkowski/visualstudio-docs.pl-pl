---
title: Symbol dostawcy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e0f01e10050fcbdb5cf27390464ae6b8b3e62d64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="symbol-provider"></a>Dostawca — symbol
Implementacja ewaluatora wyrażenia muszą uzyskać dostęp do informacji symboliczne debugowania generowanych przez kompilator języka Aby obliczyć zmiennych i wyrażeń. Robi to przez interfejsy dostawcę symbolu (SP1), nazywany również obsługi symboli.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dostarcza SPs dla kodu zarządzanego, a także kod natywny przy użyciu formatu pliku symboli bazy danych programu (PDB). Chyba że istnieje silne wymagają programu użyć symboli przechowywane w niestandardowym formacie, jest zalecane używanie SPs dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Aparatami debugowania oczekiwać Porozmawiaj z SPs przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym SP, który będzie praca z aparatami debugowania programu Visual Studio musi obsługiwać środowiska CLR. Pełna lista wszystkich debugowanie interfejsy CLR można znaleźć w debugref.doc, który jest częścią programu [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Jeśli programu SP pracować tylko z aparat debugowania niestandardowych, można zaimplementować PS zgodnie z własnymi potrzebami w zależności od potrzeb aparat debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)