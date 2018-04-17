---
title: 'CA2201: Nie wywołuj zastrzeżonych typów wyjątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd95bedc273a14d9b3d455db5fd25eac1cf74aa4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Nie wywołuj zastrzeżonych typów wyjątków
|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda zgłasza typ wyjątku, który jest zbyt ogólne lub który jest zarezerwowany przez środowisko uruchomieniowe.  
  
## <a name="rule-description"></a>Opis reguły  
 Następujące typy wyjątków są zbyt ogólne, aby zapewnić wystarczającą ilość informacji do użytkownika:  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 Następujące typy wyjątków są zarezerwowane i powinien być zgłoszony tylko przez środowisko uruchomieniowe języka wspólnego:  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Nie zgłaszają Wyjątki ogólne**  
  
 Jeśli typ ogólny wyjątek, takich jak throw <xref:System.Exception> lub <xref:System.SystemException> w bibliotece lub w ramach wymusi konsumentów, aby wykryć wszystkie wyjątki, w tym nieznany wyjątki, których nie wiadomo jak obsługiwać.  
  
 Zamiast tego należy zgłosić typu pochodnego, która już istnieje w ramach albo tworzyć własne typu pochodzącego od <xref:System.Exception>.  
  
 **Throw określonych wyjątków**  
  
 W poniższej tabeli przedstawiono parametry i wyjątków, które ma zostać zgłoszony podczas sprawdzania poprawności parametru, w tym wartość parametru metody dostępu set właściwości:  
  
|Opis parametru|Wyjątek|  
|---------------------------|---------------|  
|`null` Odwołanie|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Poza dozwolonym zakresem wartości (na przykład indeks dla kolekcji lub listy)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Nieprawidłowy `enum` wartość|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Zawiera formatu, który nie spełnia wymagań parametru metody (np. ciąg formatu w celu `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|  
|W przeciwnym razie jest nieprawidłowy|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Jeśli operacja jest nieprawidłowa dla bieżącego stanu obiektu throw <xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Po wykonaniu operacji na obiekcie, który został usunięty throw <xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Jeśli operacja nie jest obsługiwana (np. klastry obliczeniowe przesłoniętych **Stream.Write** w strumieniu otwarty do odczytu) throw <xref:System.NotSupportedException?displayProperty=fullName>  
  
 Podczas konwersji spowodowałaby przepełnienie (np. przeciążenia operatora rzutowania jawnego) throw <xref:System.OverflowException?displayProperty=fullName>  
  
 W innych sytuacjach należy rozważyć utworzenie własnych typu pochodzącego od <xref:System.Exception> i który throw.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, należy zmienić typ zwrócony wyjątek dla określonego typu, który nie jest jednym z typów zastrzeżone.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1031: Nie przechwytuj ogólnych typów wyjątków](../code-quality/ca1031-do-not-catch-general-exception-types.md)