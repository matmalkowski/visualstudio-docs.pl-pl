---
title: Zarządzane Minimum reguły dla zarządzanego kodu
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2ec566fb45b68505849639af00f85bbe81aa6f16
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Zarządzane Minimum reguły dla zarządzanego kodu
Zarządzane Minimum Rules skupić się na najpoważniejszych problemów w kodzie, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne ważne błędy logiki i projektowania. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, które posiadają pola usuwalne powinny być usuwalne|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Usuń puste finalizatory|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Pola usuwalne powinny zostać usunięte.|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Przeciąż operator equals przy zastępowaniu ValueType.Equals|
