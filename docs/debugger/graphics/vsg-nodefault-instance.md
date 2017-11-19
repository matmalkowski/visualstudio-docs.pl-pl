---
title: VSG_NODEFAULT_INSTANCE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a460110c56775723a3ab1a2933868e4508c18562
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Definiuje przez jego obecność czy domyślnego wystąpienia programu [vsgdbg — klasa](vsgdbg-class.md) klasy — która zapewnia interfejs przechwycenie programowe — podano.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Wartość  
 Preprocesora symbol jej obecności lub braku Określa, czy wystąpienie domyślne `VsgDbg` podano klasy. Jeśli ta ikona jest zdefiniowany, następnie żadne domyślne wystąpienie `VsgDbg` klasy jest dostarczana, w przeciwnym razie domyślnego wystąpienia ma być dostarczana i zainicjowany przed uruchomieniem programu.  
  
 Interfejs przechwycenie programowe jest dostarczane za pomocą wskaźnika, która ma zakres globalny, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślne wystąpienie często jest wystarczająca, ale korzystania z interfejsu przechwycenie programowe wewnątrz biblioteki DLL, po utworzeniu urządzenia D3D spoza tej biblioteki DLL, należy utworzyć i zarządzać własnego wystąpienia `VsgDbg` klasy. Jeśli zarządzasz interfejsu do programowe Przechwytywanie interfejsu API w ten sposób wyłączyć domyślnego wystąpienia, definiując `VSG_NODEFAULT_INSTANCE` Aby uniknąć zadań.  
  
 Jeśli wystąpienie domyślne nie zostanie wyłączony, automatycznie jest inicjowana przed Twojej program zostanie uruchomiony i automatycznie zostanie zniszczony podczas kończenia programu. Nie masz do inicjowania lub jawnie uninitialize tego wystąpienia.  
  
 Aby wyłączyć domyślnego wystąpienia, należy zdefiniować `VSG_NODEFAULT_INSTANCE` przed wprowadzeniem `vsgcapture.h` w programie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak wyłączyć domyślne wystąpienie:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```