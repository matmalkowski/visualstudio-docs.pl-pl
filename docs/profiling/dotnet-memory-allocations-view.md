---
title: Widok alokacji pamięci .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b293c5a6fe64324cb306933d90049548e7a6098
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="net-memory-allocations-view"></a>.NET Widok alokacji pamięci
Widok alokacji zawiera typy, które zostały utworzone podczas przebiegu profilowania. Każdy typ jest węzeł główny drzewa wywołań, który wyświetla ścieżek wykonywania funkcji, które spowodowało alokacje typu.  
  
 Dane w wierszu typu Wyświetla całkowita liczba obiektów tego typu, które zostały utworzone w przebiegu profilowania i łączna liczba bajtów przydzielonych w przypadku obiektów tego typu. Włącznie i wyłącznego wartości dla typu zawsze są takie same.  
  
-   Wartości z wartościami granicznymi są przeznaczone dla obiektów utworzonych w wystąpieniach funkcji i jej funkcji podrzędnych, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.  
  
-   Wyłączny wartości są dla obiektów, które zostały utworzone bezpośrednio przez funkcję, jeśli zostały one wywołane przez funkcję nadrzędnej. Obiektów utworzonych w funkcji podrzędnej nie są uwzględniane.  
  
 Dane dla funkcji Wyświetla liczbę obiektów utworzonych i liczba bajtów przydzielonych dla obiektów typu nadrzędnego.  
  
## <a name="highlighting-the-execution-hot-path"></a>Wyróżnianie ścieżkę aktywną wykonywania  
 Można znaleźć ścieżki wykonywania drzewa wywołań utworzony większość obiektów o typie elementu nadrzędnego.  
  
-   Aby wyświetlić najbardziej aktywne ścieżki, kliknij prawym przyciskiem myszy typu lub funkcji, a następnie kliknij przycisk **rozwiń aktywnej ścieżki**.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa przydzielonego typu lub funkcji.|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera typu lub funkcji.|  
|**Ścieżka modułu**|Ścieżka moduł zawierający typu lub funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla typu lub funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej definicji typu lub funkcji w pliku źródłowym.|  
|**poziom**|Wskazuje, czy dane dla typu lub funkcji.|  
|**Alokacje włącznie**|— Dla funkcji, całkowita liczba obiektów o typie elementu nadrzędnego, które zostały utworzone przez funkcję. Liczba ta obejmuje obiektów utworzonych w funkcji podrzędnych.<br />— Dla typu, całkowita liczba wystąpień tego typu, które zostały utworzone.|  
|**% Alokacji włącznie**|— Dla funkcji odsetek wszystkich obiektów utworzonych w przebiegu profilowania, które były włącznie alokacje typu nadrzędnego przez funkcję.<br />— W przypadku typu procent całkowitej liczby obiektów, które zostały utworzone w przebiegu, który profilowania były wystąpienia typu.|  
|**Wyłączny alokacji**|— Dla funkcji, liczbę obiektów, które zostały utworzone podczas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Ta liczba nie ma obiektów utworzonych w funkcji podrzędnych.<br />— Dla typu, całkowita liczba wystąpień tego typu, które zostały utworzone.|  
|**% Wyłącznego alokacji**|— Dla funkcji odsetek wszystkich obiektów utworzonych w przebiegu profilowania, które były wyłącznego alokacje typu nadrzędnego przez funkcję.<br />— W przypadku typu procent całkowitej liczby obiektów, które zostały utworzone w przebiegu, który profilowania były wystąpienia typu.|  
|**Bajty włącznie**|— Dla funkcji, liczba bajtów pamięci, które zostały przydzielone przez funkcję dla obiektów typu nadrzędnego. Liczba ta obejmuje pamięci, która została przydzielona przez jej funkcji podrzędnych.<br />— Dla typu całkowita liczba bajtów, które zostało przydzielone w profilowania uruchomione dla wystąpienia typu.|  
|**% Bajtów włącznie**|-Funkcja wartości procentowej pamięci wszystkie przydzielone, w którym profilowania zostało włącznie alokacje typu nadrzędnego przez funkcję.<br />— W przypadku typu wartości procentowej pamięci wszystkie przydzielone w profilowania uruchamiania, która została przydzielona do wystąpienia typu.|  
|**Wyłączny bajtów**|— Dla funkcji, liczba bajtów pamięci, które zostały przydzielone przez funkcję dla obiektów typu nadrzędnego. Ta liczba nie obejmuje pamięci, która została przydzielona przez jej funkcji podrzędnych.<br />— Dla typu całkowita liczba bajtów przydzielonych w profilowania uruchomione dla wystąpienia typu.|  
|**% Wyłącznego bajtów**|— Dla funkcji wartości procentowej pamięci wszystkie przydzielone, w którym profilowania został wyłącznego alokacje typu nadrzędnego przez funkcję.<br />— W przypadku typu wartości procentowej pamięci wszystkie przydzielone w profilowania uruchamiania, która została przydzielona do wystąpienia typu.|