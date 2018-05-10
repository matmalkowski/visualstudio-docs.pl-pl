---
title: Przykładowy kod służący do tworzenia testów jednostkowych
description: W tym artykule przedstawiono przykładowy kod, który można przetestować przy użyciu testów jednostkowych programu Visual Studio.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93a6627b96daefa48c9a72fd84726775fc449bde
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="sample-code-for-testing"></a>Przykładowy kod do testowania

Ten przykładowy kod zawiera klasę, *prezentowanie ich*, z różnych metod, które można zbadać za pomocą testów jednostkowych.

Kod jest używany w następujące wskazówki:

- [Tworzenie i Uruchamianie testów jednostkowych zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). W tym przewodniku poprowadzi Cię przez kroki tworzenia i dostosować testy jednostkowe, uruchom je i zbadanie wyników testu.
- [Za pomocą narzędzia wiersza polecenia testowego](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). W tym przewodniku używasz MSTest.exe narzędzia wiersza polecenia do uruchomienia testów i wyświetlenia wyników.

## <a name="sample-code"></a>Przykładowy kod

Tylko celowy błąd w tym przykładzie jest w metody debetowa "m_balance += kwota" powinien minus nie plus Zaloguj się przed znakiem równości.

```csharp
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

/ * Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia opisywane w przykładach są fikcyjne. Wszelkie rzeczywistą firmą, organizacji, produktu, nazwa domeny, adres e-mail, logo, osoby, miejscami lub zdarzeniami ma i zdarzeniami. \*/

## <a name="create-the-project"></a>Utwórz projekt

Aby pracować z tego kodu, najpierw Utwórz projekt dla niego w programie Visual Studio. Wykonaj kroki, aby utworzyć projekt w [wskazówki: tworzenie i Uruchamianie testów jednostkowych zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test).

## <a name="see-also"></a>Zobacz także

- [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Wskazówki: Użyj narzędzia wiersza polecenia testu](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
