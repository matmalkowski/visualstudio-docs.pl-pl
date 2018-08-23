---
title: Dane klasy dziedziczenia (Projektant O-R) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c361d35a4c5d6c4418a803b6bbba403e5571e1e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42627935"
---
# <a name="data-class-inheritance-or-designer"></a>Dziedziczenie klas danych (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [danych klasy (Projektant O-R) dziedziczenia](https://docs.microsoft.com/visualstudio/data-tools/data-class-inheritance-o-r-designer).  
  
  
Inne obiekty, takie jak [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasy można użyć dziedziczenia i pochodzić z innych klas. W kodzie można określić relacji dziedziczenia między obiektami, deklarując, że jedna klasa dziedziczy z innego. W bazie danych relacje dziedziczenia są tworzone na kilka sposobów. [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Obsługuje dziedziczenia pojedynczej tabeli, co jest często stosowana w systemach relacyjnych.  
  
 Dziedziczenie pojedynczej tabeli Brak tabeli pojedynczej bazy danych, która zawiera kolumny dla klas podstawowych i pochodnych. Z danymi relacyjnymi kolumna dyskryminatora zawiera wartość, która określa, która z klas należą wszelkie podane rekordy do. Na przykład rozważmy tabelę osoby, która zawiera wszystkich stosowanych przez firmę. Niektórzy użytkownicy są pracownicy i niektóre osoby menedżerów. Tabela osób zawiera kolumnę o nazwie typu, który ma wartość 1 dla menedżerów i wartość 2 dla pracowników. Kolumna typu jest kolumna dyskryminatora. W tym scenariuszu można utworzyć podklasę pracowników i wypełnić klasy za pomocą tylko te rekordy, które mają wartość typu 2.  
  
 Po skonfigurowaniu dziedziczenia klas jednostek za pomocą [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], przeciągnij pojedynczej tabeli, która zawiera dane dziedziczenia w Projektancie dwa razy: jeden raz dla każdej klasy w hierarchii dziedziczenia. Po dodaniu tabel do projektanta, łącz je z elementem dziedziczenia z **Object Relational Designer** przybornika, a następnie ustaw cztery właściwości dziedziczenia w **właściwości** okna.  
  
## <a name="inheritance-properties"></a>Dziedziczenie właściwości  
 W poniższej tabeli wymieniono właściwości dziedziczenia i ich opisy:  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|Właściwość rozróżniacza|Właściwość (mapowane na kolumny), która określa, która klasa należy bieżący rekord.|  
|Wartość dyskryminatora klasy bazowej|Wartość (w kolumnie, wyznaczony jako właściwość rozróżniacza), która określa, czy rekord ma klasę bazową.|  
|Wartość dyskryminatora klasy pochodnej|Wartość (w właściwość wyznaczony jako właściwość rozróżniacza), który określa, czy rekord jest klasy pochodnej.|  
|Wartość domyślna dziedziczenia|Klasa, która powinna być wypełniana podczas wartości właściwości są oznaczone jako **właściwość rozróżniacza** nie pasują do jednego **wartość dyskryminatora klasy podstawowej** lub **klasy pochodnej Wartość dyskryminatora**.|  
  
 Tworzenie modelu obiektów, która korzysta z dziedziczenia i odpowiada relacyjnej bazie danych może być nieco mylące. Ten temat zawiera informacje o podstawowych pojęć i poszczególne właściwości, które są wymagane do skonfigurowania dziedziczenia. W poniższych tematach przedstawiono bardziej zrozumiały opis sposobu konfigurowania dziedziczenia z [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|W tym artykule opisano sposób konfigurowania klas jednostek, korzystających z pojedynczej tabeli dziedziczenia przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
|[Wskazówki: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Zawiera szczegółowe instrukcje dotyczące konfigurowania klas jednostek, korzystających z pojedynczej tabeli dziedziczenia przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Wskazówki: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Wskazówki: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Wprowadzenie](http://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)

