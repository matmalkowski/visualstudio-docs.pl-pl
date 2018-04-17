---
title: 'CA2103: Przejrzyj zabezpieczenia imperatywne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5a46629efacc37af593e4cd7487b69031cf6bb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Przejrzyj zabezpieczenia imperatywne
|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda używa imperatywnych zabezpieczeń i może konstruować uprawnienia za pomocą informacji o stanie lub wartości zwrotnych, które można zmienić, dopóki żądanie jest aktywne.  
  
## <a name="rule-description"></a>Opis reguły  
 Zabezpieczenia imperatywne używa zarządzanych obiektów do określania uprawnień i akcje zabezpieczeń podczas wykonywania kodu, w porównaniu do zabezpieczenia deklaratywne, która przechowuje atrybuty uprawnienia i akcje w metadanych. Zabezpieczenia imperatywne jest bardzo elastyczne, ponieważ można ustawić stanu obiektu uprawnień i wybierz akcje zabezpieczeń przy użyciu informacji, która nie jest dostępna do czasu wykonywania. Oraz że elastyczność pochodzi ryzyko, że informacje środowiska uruchomieniowego, które można określić, że stan uprawnienia nie pozostaje bez zmian, pod warunkiem, akcja jest aktywna.  
  
 Należy używać zabezpieczeń deklaracyjnych wszędzie, gdzie to możliwe. Wymagania związane z deklaratywne są łatwiejsze do zrozumienia.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Przejrzyj zabezpieczenia imperatywne zapotrzebowanie aby upewnić się, że stan uprawnienia nie zależą od informacji tak długo, jak uprawnienie jest używana, można zmienić.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli uprawnienia nie bazuje na zmiany danych. Jednak zaleca się zmienić nadrzędnych żądanie na jej odpowiednik deklaratywne.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)   
 [Dane i modelowanie](/dotnet/framework/data/index)