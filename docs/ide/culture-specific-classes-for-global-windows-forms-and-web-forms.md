---
title: Klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3e7982b11ffba3cc48cd47488cf2258978168452
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web

Każdy kulturę różnych Konwencji do wyświetlania dat, czasu, cyfry, waluty i inne informacje. <xref:System.Globalization> Przestrzeń nazw zawiera klasy, które mogą służyć do modyfikowania wartości jak specyficzne dla kultury są wyświetlane, takich jak <xref:System.Globalization.DateTimeFormatInfo>, **kalendarza**, i <xref:System.Globalization.NumberFormatInfo>.

## <a name="using-the-culture-setting"></a>Przy użyciu ustawienia kulturowe

Użyj ustawienia kultury, przechowywane w aplikacji lub w **Opcje regionalne** Panelu sterowania, aby automatycznie określić konwencje kultury w czasie wykonywania i odpowiednio sformatować informacje. Aby uzyskać więcej informacji na temat ustawiania kultury, zobacz [porady: ustawienie kultury i kultury interfejsu użytkownika dla globalizacji strony sieci Web ASP.NET](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Klasy, które automatycznie Formatuj informacji zgodnie z ustawieniem kultury są nazywane specyficzne dla kultury. Niektóre metody specyficzne dla kultury są <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName>, i <xref:System.String.Format%2A?displayProperty=fullName>. Niektóre funkcje specyficzne dla kultury (w języku Visual Basic) są `MonthName` i `WeekDayName`.

Na przykład poniższy kod przedstawia sposób korzystania <xref:System.IFormattable.ToString%2A> metodę formacie waluty dla bieżącej kultury:

```vb
' Put the Imports statements at the beginning of the code module  
Imports System.Threading  
Imports System.Globalization  
' Display a number with the culture-specific currency formatting  
Dim MyInt As Integer = 100  
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module  
using System.Threading;  
using System.Globalization;  
// Display a number with the culture-specific currency formatting  
int myInt = 100;  
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));  
```

Jeśli kultury jest ustawiony na "fr-FR", zostanie wyświetlony to w oknie danych wyjściowych:  

`100,00`

Jeśli kultura ma ustawioną wartość "en US", zostanie wyświetlony to w oknie danych wyjściowych:  

`$100.00`

## <a name="see-also"></a>Zobacz także

<xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
<xref:System.Globalization.DateTimeFormatInfo>   
<xref:System.Globalization.NumberFormatInfo>   
<xref:System.Globalization.Calendar>   
<xref:System.Console.WriteLine%2A?displayProperty=fullName>   
<xref:System.String.Format%2A?displayProperty=fullName>   
[Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)