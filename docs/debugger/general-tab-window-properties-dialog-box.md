---
title: "Karta ogólna, okno dialogowe właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b26896ce119e49ec2d001a0b09bc7b563bd7cac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="general-tab-window-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości okna
Użyj **ogólne** kartę do wyświetlania informacji dotyczących wybranego okna. Aby wyświetlić [okno dialogowe właściwości](../debugger/window-properties-dialog-box.md), Przenieś fokus do [widoku systemu Windows](../debugger/windows-view.md) okna. Zaznacz dowolny węzeł okna w drzewie, a następnie wybierz pozycję **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **ogólne** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Tytuł okna**|Tekst w nagłówku okna lub tekst zawarty w oknie, jeśli formant.|  
|**Uchwyt okna**|Unikatowy identyfikator tego okna. Numery uchwyt okna są używane ponownie; identyfikują one okna jedynie przez czas ich istnienia tego okna.|  
|**Proces okna**|Wirtualny adres funkcji procedury okna dla tego okna. To pole wskazuje także, czy okno jest oknem Unicode i czy jest podklasą.|  
|**Prostokąt**|Prostokąt ograniczający okna. Wyświetlana jest również rozmiar prostokąta. Jednostki są pikseli współrzędne ekranu.|  
|**Rect przywrócony**|Prostokąt ograniczający przywróconej okna. Wyświetlana jest również rozmiar prostokąta. Rect przywróconej będą się różnić z prostokąt tylko wtedy, gdy okno jest zmaksymalizowane lub zminimalizowane. Jednostki są pikseli współrzędne ekranu.|  
|**Rect klienta**|Prostokąt ograniczający obszar klienta okna. Wyświetlana jest również rozmiar prostokąta. Jednostki są względem lewego górnego rogu obszaru klienckiego okna w pikselach.|  
|**Dojście wystąpienia**|Dojście wystąpienia aplikacji. Uchwyty wystąpienia nie są unikatowe.|  
|**Identyfikator formantu lub dojście Menu**|Jeśli okno jest wyświetlane jest okno podrzędne, jest wyświetlana etykieta Identyfikatora formantu. Identyfikator formantu jest liczba całkowita, która identyfikuje identyfikator formantu tego okna podrzędnego. Jeśli wyświetlane okno nie jest oknem podrzędnym, zostanie wyświetlony etykiety Menu obsługi. Dojście do menu jest liczba całkowita, która identyfikuje dojście menu skojarzone z tego okna.|  
|**Dane użytkownika**|Dane specyficzne dla aplikacji, które jest dołączony do tej struktury okna.|  
|**Okno bajtów**|Liczba bajtów dodatkowe skojarzone z tym oknem. Znaczenie tych bajtów jest określany przez aplikację. Rozwiń pole listy wartości bajtów w formacie DWORD.|