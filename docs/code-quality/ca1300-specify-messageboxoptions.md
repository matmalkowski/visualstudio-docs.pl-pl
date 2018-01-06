---
title: "CA1300: Określ MessageBoxOptions | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b47c5f2297d9b13e33dc064a203bfd84ce2d196f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Określ MessageBoxOptions
|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Kategoria|Microsoft.Globalization|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Metoda wywołuje przeciążenia <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metodę, która nie przyjmuje <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumentu.  
  
## <a name="rule-description"></a>Opis reguły  
 Aby wyświetlić okno komunikatu poprawnie dla kultury, których kolejność czytania od prawej do lewej, <xref:System.Windows.Forms.MessageBoxOptions> i <xref:System.Windows.Forms.MessageBoxOptions> członkami <xref:System.Windows.Forms.MessageBoxOptions> wyliczenia muszą być przekazywane do <xref:System.Windows.Forms.MessageBox.Show%2A> metody. Sprawdź <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> właściwości zawierającego formantu, aby ustalić, czy kolejność czytania od prawej do lewej.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, wywoływać przeciążenia <xref:System.Windows.Forms.MessageBox.Show%2A> metody pobierającej <xref:System.Windows.Forms.MessageBoxOptions> argumentu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy nie jest lokalizowany biblioteki kodu dla kultury, która używa kolejność czytania od prawej do lewej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metodę, która wyświetla komunikat, który zawiera opcje, które są odpowiednie dla kultury kolejność odczytu. Plik zasobu, który nie jest wyświetlany, jest wymagany do kompilacji w przykładzie. Postępuj zgodnie z uwagi na przykład do kompilacji w przykładzie bez pliku zasobu i testowania funkcji od prawej do lewej.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index)