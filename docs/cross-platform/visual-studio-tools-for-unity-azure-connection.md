---
title: "Visual Studio Tools for Unity Azure wskazówki połączenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: cb2ce447f21231b98d6464824ba7d088fee16cce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-client-connection"></a>Testowanie połączenia klienta

Obecnie AzureMobileServiceClient singleton został utworzony, jest czasu testu połączenia klienta.

## <a name="create-the-testclientconnection-script"></a>Utwórz skrypt TestClientConnection

1. Wewnątrz **skryptów** folderu w Unity, Utwórz nowy skrypt języka C# o nazwie **TestClientConnection**.

2. Otwórz skrypt w programie Visual Studio, usunięcie wszelkiego kodu szablonu i dodaj następujące informacje:

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. W jednolitości **GameObject** menu, wybierz opcję **GameObject > Utwórz pusty** utworzyć pusty GameObject sceny Unity. Zmień jego nazwę **TestClientConnection**.

4. **Przeciągnij** skryptu TestClientConnection z jednolitości **projektu** okna na TestClientConnection GameObject w **hierarchii** okna.

5. Wybierz z menu Unity **pliku > sceny Zapisz jako...** . Nazwa sceny **testu połączenia klienta** i kliknij przycisk **zapisać**.

5. Kliknij przycisk **odtwarzanie** przycisk Unity i sprawdź okno konsoli. Upewnij się, że żaden z potwierdzenia nie.

6. Otwórz tabelę łatwe CrashInfo w portalu Azure. Teraz powinien mieć wpis z **X, Y, Z** współrzędne **(1, 2, 3)** i wartości **true** dla w **usunięte** kolumny. Zawsze, gdy uruchomienie testu, nowy wpis o tej samej wartości, ale unikatowy identyfikator dodaje się do tabeli.

  ![Łatwe wpisu tabeli](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>Następny krok
* [Importuj przykładowe zasoby gier](visual-studio-tools-for-unity-azure-game-assets.md).
