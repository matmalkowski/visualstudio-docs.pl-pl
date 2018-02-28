---
title: Funkcja SccGet | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 73f5c55b39d855eb084206ef27e2254d50377b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccget-function"></a>Funkcja SccGet
Ta funkcja pobiera kopię co najmniej jeden plik do przeglądania i kompilacji, ale nie do edycji. Większość systemów plików są oznaczone jako tylko do odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 To  
 [in] Liczba plików określonych w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica w pełni kwalifikowane nazwy plików, które mają zostać pobrane.  
  
 fOptions  
 [in] Polecenie flagi (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Opcje plug-dotyczące kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie operacji get.|  
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_FILEISCHECKEDOUT|Nie można pobrać pliku, który użytkownik aktualnie został wyewidencjonowany.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NOSPECIFIEDVERSION|Określono nieprawidłową wersję lub daty/godziny.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; Nie można zsynchronizować pliku.|  
|SCC_I_OPERATIONCANCELED|Operacja anulowana przed ukończeniem.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma uprawnień do wykonania tej operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana z liczbą i tablicę nazw plików, które mają zostać pobrane. Jeśli IDE przekazuje flagę `SCC_GET_ALL`, oznacza to, że elementy w `lpFileNames` nie są pliki, ale katalogów, a wszystkie pliki pod kontrolą źródła w katalogach danego mają zostać pobrane.  
  
 `SCC_GET_ALL` Flagi można łączyć z `SCC_GET_RECURSIVE` flagę, aby pobrać wszystkie pliki w danym katalogów i wszystkie podkatalogi również.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`nigdy nie powinny zostać przekazane bez `SCC_GET_ALL`. Należy również zauważyć, że jeśli katalogów C:\A i C:\A\B uzyskać zarówno przekazywane na rekursywny, C:\A\B i jego podkatalogach zostanie faktycznie pobrany dwa razy. Odpowiedzialność IDE — i kontroli źródła nie dodatku plug-in — Aby upewnić się, że duplikatów, takich jak ta są przechowywane poza tablicy.  
  
 Na koniec, nawet jeśli wtyczki kontroli źródła określony `SCC_CAP_GET_NOUI` flagi podczas inicjowania i wskazujący, że nie ma interfejsu użytkownika dla polecenia Get, nadal można wywoływać tej funkcji IDE w celu pobierania plików. Flaga po prostu oznacza, że IDE nie wyświetla element menu Get i że wtyczka nie powinien zapewniać elementów interfejsu użytkownika.  
  
## <a name="renaming-and-sccget"></a>Zmiana nazwy i SccGet  
 Sytuacja: użytkownik wyewidencjonuje plik, na przykład a.txt i modyfikuje je. Przed a.txt mogą zostać zaewidencjonowane, drugi użytkownik zmienia nazwę a.txt na b.txt w bazie danych kontroli źródła, wyewidencjonuje b.txt sprawia, że niektóre zmiany w pliku i kontroli w pliku. Pierwszy użytkownik chce, aby zmiany wprowadzone przez drugiego użytkownika, aby pierwszy użytkownik zmienia nazwę ich lokalnej wersji pliku a.txt na b.txt i wykona operację pobierania na plik. Jednak lokalnej pamięci podręcznej, który śledzi numery wersji nadal sądzi pierwszej wersji a.txt są przechowywane lokalnie, a więc kontroli źródła nie może rozpoznać różnice.  
  
 Istnieją dwa sposoby rozwiązania tej sytuacji, gdy w lokalnej pamięci podręcznej wersji kontroli źródła staje się zsynchronizowane z bazy danych kontroli źródła:  
  
1.  Zezwala na zmianę nazwy pliku w bazie danych kontroli źródła, który jest obecnie wyewidencjonowywany.  
  
2.  Czy odpowiednikiem "Usuń stare" następuje polecenie "Dodaj nowy". Następujący algorytm jest jednym ze sposobów w tym celu.  
  
    1.  Wywołanie [SccQueryChanges](../extensibility/sccquerychanges-function.md) funkcji, aby dowiedzieć się więcej o zmianę a.txt do b.txt w bazie danych kontroli źródła.  
  
    2.  Zmień nazwę lokalnych a.txt b.txt.  
  
    3.  Wywołanie `SccGet` funkcja a.txt i b.txt.  
  
    4.  Ponieważ a.txt nie istnieje w bazie danych kontroli źródła, wersji lokalnej pamięci podręcznej są przeczyszczane Brak a.txt informacji o wersji.  
  
    5.  Plik b.txt wyewidencjonowany jest scalany z zawartości pliku lokalnego b.txt.  
  
    6.  Plik zaktualizowane b.txt teraz mogą zostać zaewidencjonowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)