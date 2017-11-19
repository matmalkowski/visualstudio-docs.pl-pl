---
title: "Wskazówki: Tworzenie prostego usługi WCF w formularzach systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 9dc8bc777d1818a50e727787bdf024036a5cb378
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Wskazówki: Tworzenie prostego usługi WCF w formularzach systemu Windows
W tym przewodniku pokazano, jak utworzyć prostą [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] usługi, przetestować go i do niego dostęp z aplikacji formularzy systemu Windows.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-service"></a>Tworzenie usługi  
  
#### <a name="to-create-a-wcf-service"></a>Tworzenie usługi WCF  
  
1.  Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual Basic** lub **Visual C#** węzeł i kliknij przycisk **WCF**, a następnie **WCF Biblioteka usługi**. Kliknij przycisk **OK** otworzyć projektu.  
  
     ![Projekt biblioteki usługi WCF](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Spowoduje to utworzenie działającą usługę, która może być przetestowane i uzyskać dostępu do. Następujące dwa kroki pokazują, jak może zmodyfikować domyślną metodę do użycia na inny typ danych. W rzeczywistej aplikacji należy również dodać funkcje do usługi.  
  
3.  ![Plik IService1](../data-tools/media/wcf2.png "wcf2")  
  
     W **Eksploratora rozwiązań**, kliknij dwukrotnie IService1.vb lub IService1.cs i znajdź następujący wiersz:  
  
     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]  
  
     Zmień typ `value` parametr ciągu:  
  
     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]  
  
     W powyższym kodzie, należy zwrócić uwagę `<OperationContract()>` lub `[OperationContract]` atrybutów. Te atrybuty są wymagane do dowolnej metody udostępnianych przez usługę.  
  
4.  ![Plik Service1](../data-tools/media/wcf3.png "wcf3")  
  
     W **Eksploratora rozwiązań**, kliknij dwukrotnie Service1.vb lub Service1.cs i znajdź następujący wiersz:  
  
     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]  
  
     Zmień typ parametru wartość ciągu:  
  
     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]  
  
## <a name="testing-the-service"></a>Testowanie usługi  
  
#### <a name="to-test-a-wcf-service"></a>Aby przetestować usługi WCF  
  
1.  Naciśnij klawisz **F5** do uruchamiania usługi. A **klienta testowego WCF** wyświetlany formularz i go załaduje usługi.  
  
2.  W **klienta testowego WCF** formularza, kliknij dwukrotnie **GetData()** metody w obszarze **IService1**. **GetData** kartę będą wyświetlane.  
  
     ![GetData &#40; &#41; Metoda](../data-tools/media/wcf4.png "wcf4")  
  
3.  W **żądania** wybierz opcję **wartość** pole i wpisz `Hello`.  
  
     ![Pole wartości](../data-tools/media/wcf5.png "wcf5")  
  
4.  Kliknij przycisk **Invoke** przycisku. Jeśli **ostrzeżenie o zabezpieczeniach** zostanie wyświetlone okno dialogowe, kliknij przycisk **OK**. Wynik będzie wyświetlany w **odpowiedzi** pole.  
  
     ![Wynik w polu odpowiedzi](../data-tools/media/wcf6.png "wcf6")  
  
5.  Na **pliku** menu, kliknij przycisk **zakończenia** aby zamknąć formularz testowy.  
  
## <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi  
  
#### <a name="to-reference-a-wcf-service"></a>Odwołania do usługi WCF  
  
1.  Na **pliku** menu wskaż **Dodaj** , a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual Basic** lub **Visual C#** a następnie wybierz węzeł **systemu Windows**, a następnie wybierz **Aplikacji formularzy systemu Windows**. Kliknij przycisk **OK** otworzyć projektu.  
  
     ![Projekt aplikacji Windows Forms](../data-tools/media/wcf7.png "wcf7")  
  
3.  Kliknij prawym przyciskiem myszy **WindowsApplication1** i kliknij przycisk **Dodaj odwołanie do usługi**. **Dodaj odwołanie do usługi** zostanie wyświetlone okno dialogowe.  
  
4.  W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odnajdowania**.  
  
     ![Okno dialogowe Dodaj odwołanie do usługi](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** będą wyświetlane w **usług** okienka.  
  
5.  Kliknij przycisk **OK** można dodać odwołania do usługi.  
  
#### <a name="to-build-a-client-application"></a>Do tworzenia aplikacji klienta  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Form1.vb** lub **pliku Form1.cs** otworzyć projektanta formularzy systemu Windows, jeśli nie jest jeszcze otwarty.  
  
2.  Z **przybornika**, przeciągnij `TextBox` kontroli, `Label` kontroli, a `Button` sterowania do formularza.  
  
     ![Dodawanie formantów do formularza](../data-tools/media/wcf9.png "wcf9")  
  
3.  Kliknij dwukrotnie `Button`i Dodaj następujący kod w `Click` obsługi zdarzeń:  
  
     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **WindowsApplication1** i kliknij przycisk **Ustaw jako projekt startowy**.  
  
5.  Naciśnij klawisz **F5** uruchomić projekt. Wprowadź tekst, a następnie kliknij przycisk. Zostanie wyświetlona etykieta "wprowadzona:" i tekst, który został wprowadzony.  
  
     ![Formularz jako wynik](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi Windows Communication Foundation oraz usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)