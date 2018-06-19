---
title: 'CA2003: Nie traktuj włókien jako wątków'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 799d0d04f8620c07be0583869eeba5dd760c7f70
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915542"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Nie traktuj włókien jako wątków
|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Zarządzanego wątku jest traktowana jako wątku Win32.

## <a name="rule-description"></a>Opis reguły
 Nie przyjęto założenie, że wątek Win32 jest zarządzanego wątku. Jest włókien. Środowisko uruchomieniowe języka wspólnego (CLR) zostanie uruchomiony wątków zarządzanych jako włókien w kontekście rzeczywistych wątków, które są własnością SQL. Wątki te mogą być współużytkowane między elementami AppDomain i nawet baz danych w procesie programu SQL Server. Przy użyciu zarządzanego wątku, który lokalny magazyn będzie działać, ale nie możesz użyć magazynu lokalnego wątku niezarządzanego lub założono, że kodu zostaną ponownie uruchomione w bieżącym wątku systemu operacyjnego. Nie należy zmieniać ustawienia, takie jak ustawienia regionalne wątku. Nie należy wywoływać CreateCriticalSection lub Funkcja CreateMutex przy użyciu elementu P/Invoke, ponieważ wymagają one, czy wątek, który przechodzi blokady musi również zakończyć blokady. Ponieważ to nie będzie w przypadku gdy używasz włókien, sekcje krytyczne Win32 i muteksy stanie się bezużyteczny w języku SQL. Można bezpiecznie użyć większość stanu obiektu zarządzanego System.Thread. W tym lokalny magazyn wątków zarządzanych i bieżącej kultury interfejsu użytkownika wątku. Jednak programowania powodów modelu, nie będzie mógł zmienić bieżącej kultury wątku, gdy używasz SQL; zostanie to wymuszone przez nowe uprawnienie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Sprawdź użycie wątków i odpowiednio zmień swój kod.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ta zasada nie ma pomijać.