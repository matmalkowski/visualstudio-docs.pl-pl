---
title: "Kojarzenie regionu formularza z klasą wiadomości programu Outlook | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3346b5cf096c523c9eb2c066d87a85e0d57efd94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="associating-a-form-region-with-an-outlook-message-class"></a>Kojarzenie regionu formularza z klasą wiadomości programu Outlook
  Możesz określić elementy, które program Microsoft Office Outlook wyświetlania regionu formularza przez kojarzenie regionu formularza z klasą wiadomości poszczególnych elementów. Na przykład jeśli chcesz dołączyć regionu formularza do dolnej części elementu poczty IPM można skojarzyć regionu formularza. Należy zwrócić uwagę klasy wiadomości.  
  
 Aby skojarzyć regionu formularza z klasą wiadomości, należy określić nazwę klasy wiadomości w **nowych regionów formularzy programu Outlook** kreatora lub zastosować atrybut do klasy fabryki regionu formularza.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understanding-outlook-message-classes"></a>Opis klasy wiadomości programu Outlook  
 Klasą wiadomości programu Outlook identyfikuje typ elementu programu Outlook. W poniższej tabeli wymieniono te osiem Typy standardowe elementy i nazwy klas wiadomości.  
  
|Typ elementu programu Outlook|Nazwa klasy wiadomości|  
|-----------------------|------------------------|  
|AppointmentItem|IPM. Termin|  
|ContactItem|IPM. Skontaktuj się z|  
|DistListItem|IPM. DistList|  
|JournalItem|IPM. Działanie|  
|MailItem|IPM. Uwaga|  
|PostItem|IPM. POST lub IPM. Post.RSS|  
|TaskItem|IPM. Zadanie|  
  
 Można również określić nazwy klas niestandardowych wiadomości. Niestandardowy komunikat klasy zidentyfikować niestandardowych formularzy, które zostały zdefiniowane w programie Outlook.  
  
> [!NOTE]  
>  Zastąpienie i regionów formularzy Zamień wszystkie można określić nazwę nowej klasy niestandardowego komunikatu. Nie trzeba używać nazwy klasy wiadomości istniejącego niestandardowego formularza. Nazwa klasy niestandardowego komunikatu musi być unikatowa. Jednym ze sposobów upewnij się, że nazwa jest unikatowa jest podobny do następującego konwencję nazewnictwa: \< *StandardMessageClassName*>.\< *Firmy*>.\< *MessageClassName*> (na przykład: IPM. Note.Contoso.MyMessageClass).  
  
## <a name="associating-a-form-region-with-an-outlook-message-class"></a>Kojarzenie regionu formularza z klasą wiadomości programu Outlook  
 Istnieją dwa sposoby kojarzenie regionu formularza z klasą wiadomości:  
  
-   Użyj **nowych regionów formularzy programu Outlook** kreatora.  
  
-   Stosowanie atrybutów klasy.  
  
### <a name="using-the-new-outlook-form-region-wizard"></a>Za pomocą nowego kreatora Region formularzy programu Outlook  
 Na ostatniej stronie **nowych regionów formularzy programu Outlook** kreatora można wybrać klasy standardowy komunikat i wpisz nazwy klas niestandardowych wiadomości, które chcesz skojarzyć z regionu formularza.  
  
 Klasy standardowy komunikat nie są dostępne, gdy region formularza zaprojektowano w celu zastąpienia cały formularz lub domyślna strona formularza. Można określić nazwy klas standardowy komunikat tylko w przypadku formularzy, które Dodaj nową stronę do formularza lub które są dołączane do dolnej części formularza. Aby uzyskać więcej informacji, zobacz [porady: dodawanie regionu formularza do projektu dodaj programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Aby dołączyć co najmniej jedną klasę niestandardowy komunikat, wpisz nazwy w **klas niestandardowych komunikatów, które spowoduje wyświetlenie tego regionu formularza?** pole.  
  
 Nazwy muszą być zgodne z następującymi wytycznymi:  
  
-   Użyj komunikat w pełni kwalifikowaną nazwę klasy (na przykład: "IPM. Note.Contoso").  
  
-   Użyj średników do oddzielania wielu nazw klasy wiadomości.  
  
-   Nie dołączaj standardowe klasy wiadomości programu Outlook, takie jak "IPM. Uwaga"lub"IPM. Skontaktuj się z". Uwzględnij tylko klasy wiadomości niestandardowych, takich jak "IPM. Note.Contoso".  
  
-   Nie określaj klasy podstawowej wiadomości przez samego siebie (na przykład: "IPM").  
  
-   Mniej niż 256 znaków dla każdej nazwy klasy wiadomości.  
  
 **Nowych regionów formularzy programu Outlook** Kreator sprawdza format wprowadzone po kliknięciu **Zakończ**.  
  
> [!NOTE]  
>  **Nowych regionów formularzy programu Outlook** Kreator sprawdza, czy nazwy klasy komunikatów, które należy podać są poprawne lub jest nieprawidłowa.  
  
 Po zakończeniu pracy kreatora **nowych regionów formularzy programu Outlook** Kreator dotyczy klasy regionu formularza, która zawiera określony komunikat nazwy klas atrybutów. Można również ręcznie zastosować te atrybuty.  
  
### <a name="applying-class-attributes"></a>Stosowanie atrybutów — klasa  
 Można skojarzyć regionu formularza z klasą wiadomości programu Outlook po ukończeniu **nowych regionów formularzy programu Outlook** kreatora. Aby to zrobić, dotyczą atrybuty klasy fabryki regionu formularza.  
  
 Poniższy przykład przedstawia dwa <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> atrybuty, które zostały zastosowane do klasy fabryki regionu formularza o nazwie `myFormRegion`. Pierwszy atrybut kojarzy regionu formularza z klasą standardowe wiadomości dla formularza wiadomości poczty. Drugi atrybut kojarzy regionu formularza z klasą niestandardowy komunikat o nazwie `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Atrybuty muszą być zgodne z następującymi wytycznymi:  
  
-   Dla klas niestandardowych wiadomości, użyj wiadomości w pełni kwalifikowaną nazwę klasy (na przykład: "IPM. Note.Contoso").  
  
-   Nie określaj klasy podstawowej wiadomości przez samego siebie (na przykład: "IPM").  
  
-   Mniej niż 256 znaków dla każdej nazwy klasy wiadomości.  
  
-   Nie dołączaj nazwy klasy standardowy komunikat Jeśli regionu formularza zamienia cały formularz lub domyślna strona formularza. Można określić nazwy klas standardowy komunikat tylko w przypadku formularzy, które Dodaj nową stronę do formularza lub które są dołączane do dolnej części formularza. Aby uzyskać więcej informacji, zobacz [porady: dodawanie regionu formularza do projektu dodaj programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Podczas kompilowania projektu programu Visual Studio sprawdza poprawność format nazwy klasy wiadomości.  
  
> [!NOTE]  
>  Visual Studio nie sprawdza, czy nazwy klasy komunikatów, które należy podać prawidłowy lub nieprawidłowy.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Nazwa formularza i przegląd klasy wiadomości](http://msdn.microsoft.com/library/office/ff867629.aspx)   
 [Formularzy programu Outlook i elementy współdziałania](http://msdn.microsoft.com/library/office/ff869706.aspx)  
  
  