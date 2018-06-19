---
title: Widok wywołujący wywoływany | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 973c65927e3732cff44ab8eecb684f3c75af8614
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264297"
---
# <a name="callercallee-view"></a>Widok wywołujący/wywoływany
Widok wywołujący/wywoływany Wyświetla informacje dotyczące profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki:  
  
 **Bieżąca funkcja** jest wyświetlane w środkowym siatki, a pokazuje profilowania informacji dla wybranych funkcji. Wartości obejmują wszystkie wywołania funkcji, które zostały zebrane w przebiegu profilowania.  
  
 **Funkcje, które wywołały bieżącą funkcję** jest wyświetlany w górnym siatki i zawiera liczbę wartości wybranej funkcji (bieżącego), które zostały wygenerowane przez wywołania funkcji wywołującego (nadrzędnego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i pokazuje profilowania informacje dotyczące funkcji wywoływanych (podrzędny) wybranej funkcji podczas wywoływania funkcji podrzędnych przez bieżącą funkcję.  
  
 Kolumny, które są dostępne w widok wywołujący/wywoływany zależą od metody profilowania (próbkowanie lub instrumentację), którego użyto do zbierania danych i czy zebrano danych pamięci .NET w profilowania uruchamiać.  
  
 Można wybrać inną funkcję się bieżącą funkcję w środkowej części widoku raportu, klikając jeden z funkcji, które są wyświetlane w dwóch częściach widoku. Widok raportu jest aktualizowana automatycznie, aby odzwierciedlić zmiany.  
  
 Dane można sortować, klikając nazw kolumn. Widok wywołujący/wywoływany można dodać dodatkowe kolumny. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wywołujący/wywoływany - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane kontencji](../profiling/caller-callee-view-contention-data.md)