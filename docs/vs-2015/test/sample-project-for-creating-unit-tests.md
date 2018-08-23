---
title: Przykładowy projekt dotyczący tworzenia testów jednostkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: 846783e398fc07ef4ddfff4ea1bca05f840bca81
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683983"
---
# <a name="sample-project-for-creating-unit-tests"></a>Przykładowy projekt dotyczący tworzenia testów jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [przykładowy projekt dotyczący tworzenia testów jednostkowych](https://docs.microsoft.com/visualstudio/test/sample-project-for-creating-unit-tests).  
  
Ten przykładowy kod znajduje się do użytku w poniższych instruktażach:  
  
-   [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Ten instruktaż poprowadzi Cię przez kroki, aby utworzyć i dostosować testy jednostkowe, uruchamiać je i sprawdź wyniki testu.  
  
-   [Przewodnik: Uruchamianie testów i wyświetlanie pokrycia kodu](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). W tym instruktażu przedstawiono sposób wyświetlania danych pokrycia kodu, który zawiera część kodu projektu, który jest poddawana testom.  
  
-   [Wskazówki: Korzystanie z narzędzia testu wiersza polecenia](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). W tym przewodniku umożliwia narzędzie wiersza polecenia MSTest.exe przeprowadzać testy i przeglądać wyniki.  
  
## <a name="sample-code"></a>Przykładowy kod  
 Tylko celowy błąd, w tym przykładzie jest w metody Debet "m_balance += amount" powinien minus nie znakiem plus, zaloguj się przed równości.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 / * Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia wymienione w niniejszym dokumencie są fikcyjne.  Wszelkie rzeczywistą firmą, organizacji, produktu, nazwy domeny, adres e-mail, logo, osoby, miejsca lub zdarzeń jest przeznaczone i powinno być wnioskowane. \*/  
  
## <a name="working-with-the-code"></a>Praca z kodem  
 Aby pracować przy użyciu tego kodu, najpierw należy utworzyć projekt dla niego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Postępuj zgodnie z instrukcjami w sekcji "Przygotowanie instruktażu" [wskazówki: tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Przewodnik: Uruchamianie testów i wyświetlanie pokrycia kodu](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Wskazówki: Korzystanie z narzędzia testu wiersza polecenia](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)



