---
title: "Klasa hierarchii typów symboli | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d2cb2374a33677f961fa798332ac96b6d801990b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="class-hierarchy-of-symbol-types"></a>Hierarchia klas typów symboli
W poniższej tabeli opisano typy symbol w hierarchii klasy.  
  
## <a name="symbol-types"></a>Typów symboli  
  
|Typ symbolu|Opis|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Symbol, który będzie używany do reprezentowania każdej klasy, struktury lub union.|  
|[Typ wyliczeniowy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Symbol dla typów wyliczenia.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Symbol dla typów wskaźnika.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Symbol dla tablic.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Symbol dla typów podstawowych|  
|[Typedef (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Symbol, który wprowadzono nazw dla innych typów.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Symbol, który będzie używany dla każdej klasy podstawowej typu zdefiniowane przez użytkownika (UDT).|  
|[Przyjaciel (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbol przyjaznego klasy i friend — funkcje.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbol dla każdego podpisu funkcji unikatowy.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbol dla każdego parametru do funkcji.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Symbol rozmiar tabeli wirtualnej.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Symbol dla tabeli wirtualnej.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Symbol typu zdefiniowanego przez dostawcę.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Symbol typ zdefiniowany w metadanych.|  
|[Wymiar](../../debugger/debug-interface-access/dimension.md)|Symbol wymiary tablicy.|  
  
> [!NOTE]
>  Każdy może mieć właściwości, które zawierają informacje dotyczące symboli oraz dla odwołania do innych symboli. Te właściwości są wyświetlane w tematach pojedynczy symbol.  
  
## <a name="see-also"></a>Zobacz też  
 [Cv_access_e — wyliczenie](../../debugger/debug-interface-access/cv-access-e.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)