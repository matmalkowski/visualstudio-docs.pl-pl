---
title: "Przykładowy projekt dotyczący tworzenia testów jednostkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: "30"
ms.author: douge
manager: douge
ms.openlocfilehash: a3ab1b6abf1949dd2c3a6afcca2987ebcf1594b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="sample-project-for-creating-unit-tests"></a>Przykładowy projekt dotyczący tworzenia testów jednostkowych
Ten przykładowy kod jest dostępne w celu użycia w następujące wskazówki:  
  
-   [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). W tym przewodniku poprowadzi Cię przez kroki tworzenia i dostosować testy jednostkowe, uruchom je i zbadanie wyników testu.  
  
-   [Wskazówki: Uruchom testy i wyświetlać pokrycie kodu](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). W tym przewodniku przedstawiono sposób wyświetlania danych pokrycia kodu, który zawiera część kodu projektu, który jest poddawana testom.  
  
-   [Wskazówki: Korzystanie z narzędzia testu w wierszu polecenia](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). W tym przewodniku używasz MSTest.exe narzędzia wiersza polecenia do uruchomienia testów i wyświetlenia wyników.  
  
## <a name="sample-code"></a>Przykładowy kod  
 Tylko celowy błąd w tym przykładzie jest w metody debetowa "m_balance += kwota" powinien minus nie plus Zaloguj się przed znakiem równości.  
  
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
  
 / * Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia opisywane w przykładach są fikcyjne.  Wszelkie rzeczywistą firmą, organizacji, produktu, nazwa domeny, adres e-mail, logo, osoby, miejscami lub zdarzeniami ma i zdarzeniami. \*/  
  
## <a name="working-with-the-code"></a>Praca z kodem  
 Aby pracować z tego kodu, najpierw należy utworzyć projekt dla niego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Wykonaj kroki opisane w sekcji "Przygotowanie wskazówki" [wskazówki: tworzenie i uruchomionych testów jednostkowych dla zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Wskazówki: Uruchom testy i wyświetlać pokrycie kodu](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Wskazówki: Korzystanie z narzędzia testu w wierszu polecenia](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
