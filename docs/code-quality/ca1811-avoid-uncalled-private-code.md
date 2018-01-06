---
title: "CA1811: Unikaj niewywołanego kodu prywatnego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 97f285a36e502edfd689ec010c8f8982fc1370ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Unikaj niewywołanego kodu prywatnego
|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Prywatny lub wewnętrzny elementu członkowskiego (poziomu zestawu) nie ma obiektów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez obiekt delegowany. Następujące elementy członkowskie nie są sprawdzane przez tę regułę:  
  
-   Elementy członkowskie interfejsu jawnego.  
  
-   Konstruktory statyczne.  
  
-   Konstruktory serializacji.  
  
-   Metody oznaczone atrybutami <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Elementy członkowskie, które są zastąpienia.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada może raportować się, że wyniki fałszywie dodatnie, jeśli wystąpią punkty wejścia, które nie zostaną rozpoznane przez logikę reguł. Ponadto kompilatora może wyemitować kodu noncallable w zestawie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Usuń noncallable kod lub Dodaj kod, który wywołuje go.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)