---
title: Zaawansowane ustawienia kompilacji — okno dialogowe (C#) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1a793d20a8d8e0a2773756da32ea252ef200e36c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632650"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Zaawansowane ustawienia kompilacji (C#) — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [zaawansowane kompilacji okno dialogowe Ustawienia (C#)](https://docs.microsoft.com/visualstudio/ide/reference/advanced-build-settings-dialog-box-csharp).  
  
  
Użyj **ustawienia AdvancedBuild** okna dialogowego **projektanta projektu** określić najbardziej zaawansowane właściwości konfiguracji kompilacji projektu. Dotyczy to okno dialogowe [!INCLUDE[csprcs](../../includes/csprcs-md.md)] wyłącznie dla projektów.  
  
## <a name="general"></a>Ogólne  
 Poniższe opcje umożliwiają konfigurowanie ogólnych ustawień zaawansowanych.  
  
 **Wersja językowa**  
 Określa wersję języka. Zestaw funkcji różni się w każdej wersji, ta opcja może służyć do wymusić na kompilatorze, aby zezwolić tylko podzbiór funkcji zaimplementowano lub włączyć tylko te funkcje, które są zgodne ze standardem istniejących. To ustawienie ma następujące opcje:  
  
-   **ISO-1**  
  
     Jest przeznaczony dla funkcji standard ISO-1.  
  
-   **default**  
  
     Jest przeznaczony dla bieżącej wersji.  
  
 Aby uzyskać więcej informacji, zobacz [/langversion (opcje kompilatora C#)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).  
  
 **Wewnętrznych kompilatora raportowanie błędów**  
 Określa, czy należy zgłaszać błędy kompilatora do firmy Microsoft. Jeśli ustawiono **wiersza** (ustawienie domyślne), jeśli zostanie wyświetlony monit o wystąpi błąd wewnętrzny kompilatora, co daje możliwość elektronicznie wysłaniem raportu o błędach do firmy Microsoft. Jeśli ustawiono **wysyłania**, raport o błędzie zostanie automatycznie wysłane. Jeśli ustawiono **kolejki**, raporty o błędach zostanie umieszczona w kolejce. Jeśli ustawiono **Brak**, błąd jest zgłaszany tylko na kompilatora tekst wyjściowy. Aby uzyskać więcej informacji, zobacz [/errorreport (opcje kompilatora C#)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).  
  
 **Sprawdzaj przepełnienie/niedopełnienie arytmetyczne**  
 Określa, czy liczba całkowita arytmetyczne instrukcja, nie jest w zakresie [zaznaczone](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) lub [unchecked](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) słów kluczowych i że wyniki w wartość spoza zakresu typu danych spowoduje, że środowiska wykonawczego wyjątek. Aby uzyskać więcej informacji, zobacz [/ checked (opcje kompilatora C#)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).  
  
 **Nie odwołuj się do biblioteki mscorlib.dll**  
 Określa, czy biblioteka mscorlib.dll zostaną zaimportowane do programu, definiując całą <xref:System> przestrzeni nazw. Zaznacz to pole wyboru, jeśli chcesz zdefiniować lub utworzyć własne <xref:System> przestrzeni nazw i obiektów. Aby uzyskać więcej informacji, zobacz [/nostdlib (opcje kompilatora C#)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).  
  
## <a name="output"></a>Dane wyjściowe  
 Poniższe opcje umożliwiają określenie opcji zaawansowanych danych wyjściowych.  
  
 **Informacje debugowania**  
 Określa typ informacji o debugowaniu generowanych przez kompilator. Aby uzyskać informacje dotyczące sposobu konfigurowania wydajność debugowania aplikacji, zobacz [ułatwianie obrazu do debugowania](http://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). To ustawienie ma następujące opcje:  
  
-   **Brak**  
  
     Określa, że będą generowane nie informacje o debugowaniu  
  
-   **full**  
  
     Umożliwia dołączanie debugera do uruchomionego programu.  
  
-   **"pdbonly"**  
  
     Umożliwia kodu źródłowego, debugowanie, gdy program jest uruchomiony w debugerze, ale będą wyświetlane tylko asemblera, gdy uruchomiony program jest dołączony do debugera.  
  
 Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).  
  
 **Wyrównanie pliku**  
 Określa rozmiar sekcji w pliku wyjściowym. Prawidłowe wartości to **512**, **1024**, **2048**, **4096**, i **8192**. Te wartości są mierzone w bajtach. Każda sekcja będzie wyrównany na granicy, która jest wielokrotnością liczby tę wartość, mających wpływ na rozmiar pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/filealign (opcje kompilatora C#)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).  
  
 **Adres podstawowy DLL**  
 Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] środowiska uruchomieniowego języka wspólnego. Aby uzyskać więcej informacji, zobacz [/baseAddress (opcje kompilatora C#)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)   
 [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)



