---
title: "Tworzenie kodowanego interfejsu użytkownika testów oczekiwania dla określonych zdarzeń podczas odtwarzania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 4a6c7ae9f0438d440471bc9e049b539e96e63e13
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Wstrzymywanie kodowanych testów użytkownika dla określonych zdarzeń podczas odtwarzania
Podczas odtwarzania testu kodowanego interfejsu użytkownika można nakazać testu czekać na niektóre zdarzenia, takie jak okna pojawia się paska postępu zniknąć i tak dalej. Aby to zrobić, użyj odpowiedniej metody UITestControl.WaitForControlXXX(), zgodnie z opisem w poniższej tabeli. Na przykład kodowanego testu interfejsu użytkownika, który oczekuje na formantu można włączyć za pomocą <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> metody, zobacz [wskazówki: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 **Wymagania**  
  
 Visual Studio Enterprise  
  
> [!TIP]
>  Można również dodać opóźnienia przed akcji za pomocą edytora kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [porady: wstawianie opóźnienia przed interfejsu użytkownika akcji za pomocą edytora kodowanego testu interfejsu użytkownika](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0).  
  
 **Metody UITestControl.WaitForControlXXX()**  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>  
  
 Czeka na formantu ma być gotowy do przyjęcia myszy i klawiatury. Aparat niejawnie wywołuje ten interfejs API dla wszystkich akcji oczekiwania kontrolka będzie gotowa, przed wykonaniem żadnej operacji. Jednak w niektórych wybór scenariusza możesz może być jawnym wywołaniem.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>  
  
 Oczekuje dla formantu, który ma być włączony, jeśli Kreator jest weryfikacja niektórych asynchroniczne danych wejściowych przez nawiązywanie połączeń z serwerem. Na przykład można metody oczekiwania **dalej** przycisk kreatora, aby być (włączone). Na przykład tej metody, zobacz [wskazówki: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>  
  
 Czeka na formancie widoczne w Interfejsie użytkownika. Na przykład po aplikacji przeprowadził weryfikację parametrów są oczekiwane okna dialogowego błędu. Czas poświęcony na sprawdzania poprawności jest zmienną. Ta metoda umożliwia oczekiwania dla okna dialogowego błędu.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>  
  
 Czeka na kontrolki są usuwane z interfejsu użytkownika. Na przykład możesz poczekać paska postępu zniknąć.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>  
  
 Czeka na określonej właściwości formantu, aby mieć podanej wartości. Na przykład należy poczekać, tekst stanu zmienić **gotowe**.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>  
  
 Czeka na określonej właściwości formantu, aby mieć przeciwieństwem określoną wartość. Na przykład po odczekaniu pole edycji, aby nie może być tylko do odczytu, oznacza to, że można edytować.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>  
  
 Czeka na określony predykat zwraca się `true`. Można to operacji oczekiwania złożonych (takich jak warunki lub) na dany formant. Na przykład możesz poczekać, aż tekst stanu będzie miał wartość **Następujący** lub **Błąd**, jak pokazano w poniższym kodzie:  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDone(UITestControl control)   
{   
    WinText statusText = control as WinText;   
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";   
}   
  
// In test method, wait till the method evaluates to true   
statusText.WaitForControlCondition(IsStatusDone);  
  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>  
  
 Wszystkie poprzednie metody to metody wystąpienia UITestControl. Ta metoda jest metodą statyczną. Ta metoda również czeka na określony predykat jako `true` , ale może służyć do operacji oczekiwania złożonych (takich jak warunki lub) na wielu formantów. Można na przykład, poczekaj aż tekst stanu **zakończyło się pomyślnie** lub dopóki nie zostanie wyświetlony komunikat o błędzie, jak pokazano w poniższym kodzie:  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDoneOrError(UITestControl[] controls)   
{   
    WinText statusText = controls[0] as WinText;   
    WinWindow errorDialog = controls[1] as WinWindow;   
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;   
}   
  
// In test method, wait till the method evaluates to true   
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);  
  
```  
  
 Wszystkie te metody mają następujące zachowanie:  
  
 Metody zwrócić wartość true, jeśli czas oczekiwania jest zakończona pomyślnie i wartość false, jeśli nie powiodła się.  
  
 Niejawne limitu czasu dla operacji oczekiwania jest określona przez <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> właściwości. Wartość domyślna tej właściwości to 60000 milisekund (jedną minutę).  
  
 Metody mają przeciążenia podjęcie jawne limitu czasu w milisekundach. Jednak gdy niejawnego wyszukiwania dla formantu, lub gdy aplikacja jest zajęta wynikiem operacji oczekiwania, czas oczekiwania rzeczywiste może być więcej niż limit czasu określony.  
  
 Poprzednie funkcje są wydajne i elastyczne i powinny spełniać prawie wszystkie warunki. Jednak w przypadku tych metod nie spełniają potrzeb i trzeba kodu albo <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A>, lub <xref:System.Threading.Thread.Sleep%2A> w kodzie, zaleca się użycie Playback.Wait() zamiast Thread.Sleep() interfejsu API. Są to:  
  
 Można użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>właściwości można modyfikować za pomocą trybu uśpienia. Domyślnie ta zmienna ma wartość 1, ale można zwiększyć lub zmniejszyć, aby zmienić czas oczekiwania na całym kodzie. Na przykład jeśli testujesz w szczególności za pośrednictwem wolno działającą sieć lub innym przypadku spadek wydajności, można zmienić tej zmiennej w jednym miejscu (lub nawet w pliku konfiguracji) do wersji 1.5, aby dodać dodatkowe 50% czekać na wszystkich miejscach.  
  
 Playback.Wait() wewnętrznie wywołuje Thread.Sleep() (po powyżej obliczeń) w mniejszych fragmentów w pętli for podczas sprawdzania, czy operacja cancel\break użytkownika. Innymi słowy umożliwia Playback.Wait() anulować odtwarzania przed końcem czas oczekiwania, natomiast w stan uśpienia może nie lub zgłoszenie wyjątku.  
  
> [!TIP]
>  Edytor kodowanego testu interfejsu użytkownika pozwala łatwo zmodyfikować kodowanych testów interfejsu użytkownika. Za pomocą edytora testu interfejsu użytkownika na stałe, można znaleźć, Wyświetl i Edytuj metody testu. Można również edytować działania interfejsu użytkownika i ich skojarzonych formantów w formancie mapy interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [testów interfejsu użytkownika kodowany edycji za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
 **Wskazówki**  
  
 Aby uzyskać dodatkowe informacje, zobacz [testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Wskazówki: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Porady: wstawianie opóźnienia przed akcją UI za pomocą edytora testu kodowanego interfejsu użytkownika](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0)
