---
title: 'CA1725: Nazwy parametrów powinny pasować do podstawowej deklaracji | Dokumentacja firmy Microsoft'
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
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 20a7e5f0239d572ec1867ffdac80f116cfd8360a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902498"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Nazwy parametrów powinny pasować do podstawowej deklaracji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1725: nazwy parametrów powinny pasować do podstawowej deklaracji](https://docs.microsoft.com/visualstudio/code-quality/ca1725-parameter-names-should-match-base-declaration).

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa parametru w widocznej zewnętrznie metodzie zastąpienia jest niezgodny z nazwy parametru w deklaracji podstawowej metody lub nazwę parametru w deklaracji metody interfejsu.

## <a name="rule-description"></a>Opis reguły
 Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zmień nazwę parametru, aby pasować do deklaracji podstawowej. Poprawka jest istotną zmianę dla metody widoczne dla modelu COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, z wyjątkiem metody widoczne dla modelu COM w bibliotekach, które wcześniej zostały wprowadzone do użytku.



