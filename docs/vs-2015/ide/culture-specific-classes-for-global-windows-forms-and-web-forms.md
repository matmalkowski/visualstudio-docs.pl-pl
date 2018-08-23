---
title: Klasy specyficzne dla kultury, globalne Windows Forms i formularzy sieci Web | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32de77cc098158f0775b3af378272542f8fd7d4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42696778"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Każda kultura ma różnych Konwencji do wyświetlania daty, godziny, liczby, waluty i inne informacje. <xref:System.Globalization> Przestrzeń nazw zawiera klasy, które mogą służyć do modyfikowania wartości jak specyficzne dla kultury są wyświetlane, takich jak <xref:System.Globalization.DateTimeFormatInfo>, **kalendarza**, i <xref:System.Globalization.NumberFormatInfo>.  
  
## <a name="using-the-culture-setting"></a>Za pomocą ustawienia kulturowe  
 Jednak w większości przypadków będzie używać ustawienia kulturowe, przechowywane w aplikacji lub w **Opcje regionalne** Panelu sterowania, aby automatycznie określić Konwencji w czasie wykonywania i odpowiednio sformatować dane. Aby uzyskać więcej informacji na temat ustawiania kultury, zobacz [porady: Ustawianie kultury i kultury interfejsu użytkownika dla Windows Forms globalizacji](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0) lub [porady: Ustawianie kultury i kultury UI dla globalizacji strony sieci Web platformy ASP.NET](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0). Klasy, które automatycznie Formatuj informacje zgodnie z ustawieniem kultury są nazywane specyficzne dla kultury. Niektóre metody specyficzne dla kultury są <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName>, i <xref:System.String.Format%2A?displayProperty=fullName>. Niektóre funkcje specyficzne dla kultury (w języku Visual Basic) są `MonthName` i `WeekDayName`.  
  
 Na przykład, poniższy kod przedstawia, jak można użyć <xref:System.IFormattable.ToString%2A> metodę format waluty bieżącej kultury:  
  
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
  
 Jeśli kultury jest ustawiona na "fr-FR", pojawią się to w oknie danych wyjściowych:  
  
 `100,00`  
  
 Jeśli kultura ma wartość "en US", pojawią się to w oknie danych wyjściowych:  
  
 `$100.00`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)

