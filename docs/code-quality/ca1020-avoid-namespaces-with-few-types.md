---
title: 'CA1020: Unikaj przestrzeni nazw z kilkoma typami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a90f43735092591ad019fd2a46569e9302cf0c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Unikaj przestrzeni nazw z kilkoma typami
|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Przestrzeń nazw innej niż globalna przestrzeń nazw zawiera mniej niż pięć typów.  
  
## <a name="rule-description"></a>Opis reguły  
 Upewnij się, czy każdy obszary nazw logiczną organizację, a typy istnienie prawidłowej przyczyny mają zostać umieszczone w słabo wypełnionego obszaru nazw. Przestrzenie nazw powinien zawierać typy, które są używane razem w większości przypadków. Po ich aplikacji wzajemnie się wykluczają, typy powinien znajdować się w oddzielnych przestrzeniach nazw. Na przykład <xref:System.Web.UI> przestrzeń nazw zawiera typy, które są używane w aplikacji sieci Web i <xref:System.Windows.Forms> przestrzeń nazw zawiera typy, które są używane w [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]— na podstawie aplikacji. Mimo że obu tych przestrzeni nazw ma typy sterujące aspektów interfejsu użytkownika, te typy nie są przeznaczone do użycia w tej samej aplikacji. W związku z tym znajdują się one w oddzielnych przestrzeniach nazw. Organizacji dokładne przestrzeni nazw można także przydatne, ponieważ zwiększa możliwość odnajdowania funkcji. Sprawdzając hierarchii obszaru nazw konsumentów biblioteki powinien być zlokalizowany typów, które implementują funkcji.  
  
> [!NOTE]
>  Typy w czasie projektowania i uprawnienia nie powinny zostać scalone w innych przestrzeniach nazw do wykonania Niniejsze wytyczne. Te typy znajdują się w ich własnych przestrzenie nazw poniżej głównej przestrzeni nazw, a przestrzenie nazw powinny kończyć się `.Design` i `.Permissions`odpowiednio.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, spróbuj połączyć przestrzenie nazw, które zawierają tylko kilka typów w jednej przestrzeni nazw.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli przestrzeń nazw nie zawiera typy, które są używane z typami w Twojej przestrzeni nazw.