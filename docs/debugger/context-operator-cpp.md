---
title: Operator kontekstu debugera (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1cae22698a0200dc0971f45dbcfd7b28005f8f0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Operator kontekstu w debugerze programu Visual Studio (C++)
Aby zakwalifikować lokalizacji punktu przerwania, nazwa zmiennej lub wyrażenie można użyć operatorze kontekstu w języku C++. Operator kontekstu jest przydatne w przypadku określenia nazwy z zewnętrznym zakresie, w przeciwnym razie ukryte przez nazwę lokalną.  
  
##  <a name="BKMK_Using_context_operators_to_specify_a_symbol"></a>Składnia  
 Istnieją dwa sposoby Określanie kontekstu:  
  
1.  {,, [*modułu*]} *wyrażenia*  
  
     Nawiasy klamrowe musi zawierać dwa przecinkami i modułu (pliku wykonywalnego lub DLL) nazwa lub pełną ścieżkę.  
  
     Na przykład, aby ustawić punkt przerwania w `SomeFunction` funkcja EXAMPLE.dll:  
  
    ```C++  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2.  *Moduł*! *wyrażenie*  
  
    ```C++  
    EXAMPLE.dll!SomeFunction  
    ```  
  
-   *Moduł* jest nazwą modułu. Pełna ścieżka służy do odróżniania między modułami o takiej samej nazwie.  
  
     Jeśli *modułu* ścieżka zawiera przecinek, osadzonych spacji ani nawiasu klamrowego, należy użyć ścieżki w cudzysłowie, aby analizator kontekstu poprawnie rozpoznać ciągu. Pojedynczy znaki cudzysłowu są traktowane jako część nazwy pliku systemu Windows, należy użyć podwójnego cudzysłowu. Na przykład  
  
    ```C++  
    {,,"a long, long, library name.dll"} g_Var  
    ```  
  
-   *wyrażenie* dowolne prawidłowe wyrażenie języka C++, który jest rozpoznawany jako prawidłowego elementu docelowego, takie jak nazwa funkcji, nazwa zmiennej lub adres wskaźnika w *modułu*.  
  
 Gdy ewaluatora wyrażenia napotka symbol w wyrażeniu, wyszukiwanie symboli w następującej kolejności:  
  
1.  Zakres leksykalne na zewnątrz, począwszy od bieżący blok, serię instrukcji ujęta w nawiasy klamrowe i na zewnątrz kontynuowanie otaczającym bloku. Bieżący blok jest kod zawierający bieżącą lokalizację adres wskaźnika instrukcji.  
  
2.  Zakres funkcji. Bieżąca funkcja.  
  
3.  Zakres klasy, jeśli bieżąca lokalizacja znajduje się wewnątrz funkcji Członkowskich C++. Zakres klasy obejmuje wszystkie klasy podstawowe. Ewaluator wyrażeń używa reguł dominacja normalnego.  
  
4.  Symbole globalne w bieżącego modułu.  
  
5.  Symbole publiczne w bieżącym programem.