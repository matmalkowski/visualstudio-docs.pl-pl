---
title: 'CA1724: Nazwy typów nie powinny odpowiadać nazwom | Dokumentacja firmy Microsoft'
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
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5028646e5c937caad60a35e67ab9935a5755929a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900225"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Nazwy typów nie powinny odpowiadać nazwom pól
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1724: typ nazwy powinny nie dopasowanie przestrzenie nazw](https://docs.microsoft.com/visualstudio/code-quality/ca1724-type-names-should-not-match-namespaces).

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa typu odpowiada [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nazwy przestrzeni nazw w porównania bez uwzględniania wielkości liter.

## <a name="rule-description"></a>Opis reguły
 Nazwy typów nie powinny odpowiadać nazwom przestrzeni nazw, które są zdefiniowane w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] biblioteki klas. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę typu, który nie jest zgodna z nazwą elementu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] biblioteki klas w przestrzeni nazw.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W nowych wdrożeniach Brak znanego scenariusze wystąpić, gdy trzeba Pomijaj ostrzeżeń dla tej reguły. Zanim można pominąć to ostrzeżenie, zastanów się, jak użytkownicy biblioteki mogą być pomylone według tej nazwy. Do wysłania biblioteki, trzeba będzie Pomijaj ostrzeżeń dla tej reguły.



