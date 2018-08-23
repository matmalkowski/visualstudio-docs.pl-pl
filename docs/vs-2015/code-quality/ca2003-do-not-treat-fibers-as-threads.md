---
title: 'CA2003: Nie Traktuj włókien jak wątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e510dc73d0e42830137a053522ed9911eef42987
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680478"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Nie traktuj włókien jako wątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2003: nie Traktuj włókien jak wątków](https://docs.microsoft.com/visualstudio/code-quality/ca2003-do-not-treat-fibers-as-threads).  
  
Element TypeName | DoNotTreatFibersAsThreads |  
| CheckId | CA2003 |  
| Kategoria | Microsoft.Reliability|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Zarządzane zarządzalny wątek jest traktowany jako wątek Win32.  
  
## <a name="rule-description"></a>Opis reguły  
 Nie należy zakładać, że wątków zarządzanych jest wątek Win32. Jest włókien. Środowisko uruchomieniowe języka wspólnego (CLR) zostanie uruchomione wątki zarządzane jako włókien w kontekście rzeczywistych wątki, które są własnością SQL. Te wątki mogą być współużytkowane przez nawet baz danych i domen aplikacji w procesie programu SQL Server. Za pomocą zarządzanych wątków, działają magazynu lokalnego, ale nie możesz użyć pamięci lokalnej wątku niezarządzanym lub przyjęto założenie, że Twój kod zostaną ponownie uruchomione w bieżącym wątku systemu operacyjnego. Nie należy zmieniać ustawienia, takie jak ustawienia regionalne wątku. Nie należy wywoływać CreateCriticalSection lub Funkcja CreateMutex za pośrednictwem metody P/Invoke, ponieważ wymagają one, wątek, który wprowadzi blokadę należy również zamknąć blokady. Ponieważ to nie będzie w przypadku gdy używasz włókien, sekcje krytyczne Win32 i Muteksy są bezużyteczne w języku SQL. Bezpiecznie mogą korzystać z większości stan zarządzanego obiektu System.Thread. Obejmuje to lokalny magazyn wątków zarządzanych i bieżącej kultury interfejsu użytkownika wątku. Jednak podczas programowania modelu przyczyny, nie będzie można zmienić bieżącej kultury wątku, gdy używasz programu SQL; będzie to wymuszane za pośrednictwem nowych uprawnień.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Sprawdź użycie wątków i odpowiednio zmień swój kod.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Ta zasada nie ma pomijać.



