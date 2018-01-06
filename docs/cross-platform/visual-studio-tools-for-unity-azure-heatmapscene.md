---
title: "Visual Studio Tools for Unity Azure wskazówki HeatmapScene | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 472b6d5adae5e23007b9c1aa4d9c75118a94e1cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="heatmapscene-explanation"></a>Wyjaśnienie HeatmapScene

HeatmapScene zawiera wystąpienie **LevelGeometry** prefab. W ten sposób współrzędne awarii ładowane z platformy Azure poprawnie mapowane na poziomie kompozycji.

## <a name="heatmap-script"></a>Skrypt Heatmap

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync`łączy do tabeli łatwe CrashInfo na platformie Azure i używa <a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx"> `ToListAsync` </a> jest dodanie wszystkich zawartych w nim wpisów do listy.

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
`SpawnMarkersFromList`iteruje po liście awarię, otrzymał od usługi Azure i tworzy prefab znacznika awarii, dla każdego wpisu.

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

`DeleteCrashDataAsync`jest wywoływane, gdy użytkownik naciśnie **Wyczyść dane** przycisku. Jego iterację lokalnej listy awarii i wywołania <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx"> `DeleteAsync` </a> dla każdego wpisu. To ustawienie każdego wpisu **usunięte** kolumny w tabeli łatwe **true**. `ToListAsync`ignoruje te wpisy usunięte.

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>Następny krok

* [Objaśnienie LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)