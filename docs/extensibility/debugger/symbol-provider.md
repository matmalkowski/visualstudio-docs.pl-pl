---
title: Symbol dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a98a5b80126bcb11109acedc2d24f226cde3714a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126176"
---
# <a name="symbol-provider"></a>Dostawca — symbol
Implementacja ewaluatora wyrażenia muszą uzyskać dostęp do informacji symboliczne debugowania generowanych przez kompilator języka Aby obliczyć zmiennych i wyrażeń. Robi to przez interfejsy dostawcę symbolu (SP1), nazywany również obsługi symboli.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza SPs dla kodu zarządzanego, a także kod natywny przy użyciu formatu pliku symboli bazy danych programu (PDB). Chyba że istnieje silne wymagają programu użyć symboli przechowywane w niestandardowym formacie, jest zalecane używanie SPs dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Aparatami debugowania oczekiwać Porozmawiaj z SPs przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym SP, który będzie praca z aparatami debugowania programu Visual Studio musi obsługiwać środowiska CLR. Pełna lista wszystkich debugowanie interfejsy CLR można znaleźć w debugref.doc, który jest częścią programu [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Jeśli programu SP pracować tylko z aparat debugowania niestandardowych, można zaimplementować PS zgodnie z własnymi potrzebami w zależności od potrzeb aparat debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)