---
title: "Visual Studio Tools for Unity Azure wskazówki RaceScene | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 304fb69ab6e5da058cd3d2a4d6de202fa042b8f9
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="racescene-explanation"></a>Wyjaśnienie RaceScene

RaceScene używa Unity [standardowe zasoby](https://www.assetstore.unity3d.com/en/#!/content/32351) utworzenie gry wyścigowych podstawowe i poziom. W tej sekcji odpowiednich GameObjects i ich skryptów opisano w kolejności, w jakiej występują w hierarchii RaceScene wyświetlaną na poniższym zrzucie ekranu.

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

**MultipurposeCameraRig** z **kamer** standardowe zasoby pakietu. Jego Inspektora właściwości mają została dostosowana do wykonaj samochodu w odpowiedniej szybkości.

## <a name="levelgeometry"></a>LevelGeometry

LevelGeometry prefab jest pusty GameObject używane w organizacji. Jego podrzędny GameObjects tworzą rozgrywane miejsca. Piętra ściany, rampy, przeszkód są tworzone z prefabs w **Prototypowania** standardowe zasoby pakietu.

**Ważna uwaga jeden** jest, że w kolejności dla obiektu pod kątem awarii, które są rejestrowane na platformie Azure, musi mieć **Wall** Znacznik zastosowany.

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Samochodu

**Samochodu** prefab pochodzi z **pojazdów** standardowe zasoby pakietu. Modyfikacja tylko jest to, że **RecordCrashInfo** dodawania składnika skryptu.

### <a name="recordcrashinfo"></a>RecordCrashInfo

Ten skrypt sprawdza, czy awarii w `OnCollisionEnter` i zapisuje je do listy. `crashRecordingCooldown`i `crashRecordingMinVelocity` ograniczenia co gry uwzględnia awarii w celu zachowania odpowiedniego zestawu danych.

Gdy `RaceFinished` zdarzenie jest zgłaszane, `UploadNewCrashDataAsync` wysyła każdego awarii na liście do tabeli łatwe CrashInfo na platformie Azure.

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>Punkty kontrolne

Poziom ma cztery GameObjects z **punktu kontrolnego** składnik skryptów. Punkty kontrolne upewnij się, że odtwarzacz nie może zakończyć wyścigu w niewłaściwy sposób dół ścieżce podróży. One również Wykryj, kiedy odtwarzacz zakończy wyścigu. Jest to, gdy `RaceFinished` zdarzenie jest wywoływane.

## <a name="invisible-collision"></a>Niewidoczne kolizji

Standardowe moduły pierwotnych z ich wyłączona składników MeshRenderer są używane jako kolizji niewidoczne do zachowania inbounds odtwarzacza. Ponadto **Bouncy** materiałów fizycznych jest stosowany w celu zapewnienia latania podskokiem samochodów od ścian niewidoczne w sposób spełniającą i zapobiec player naciśnięcie wall niewidoczne, przedłużanie dół go i kierowanych na górze widoczne tablicy.

## <a name="recordhighscore"></a>RecordHighScore

Ten skrypt sprawdza, jeśli odtwarzacz ma zdobytych nowe najlepszy wynik. Jeśli są dostępne, wyświetla `enterNamePopup`, dzięki czemu odtwarzacz, aby wprowadzić odpowiednią nazwę, a następnie kliknij przycisk **przesyłania**.

Złożone nazwy player `UploadNewHighScoreAsync` nosi nazwę i nowe najlepszy wynik są wysyłane do tabeli łatwe HighScoreInfo na platformie Azure.

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>Następny krok

* [Wyjaśnienie HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md).
