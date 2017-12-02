# <a name="create-an-ai-project-from-existing-code"></a>Tworzenie projektu AI z istniejącego kodu

Po wprowadzeniu [zainstalowany program Visual Studio Tools dla AI](installation.md), łatwo ją przenieść istniejący kod języka Python do projektu programu Visual Studio. 

> [!Important]
>
> Proces opisany w tym miejscu nie Przenieś lub skopiuj oryginalnych plików źródłowych. Jeśli chcesz pracować z kopią, najpierw zduplikowane folderu.

1. Uruchom program Visual Studio i wybierz **Plik > Nowy > Projekt**.

1. W **nowy projekt** okno dialogowe, wyszukaj "**narzędzia AI**", wybierz pozycję "**kodu z istniejących Python**" szablonu, nadaj projektu, nazwy i lokalizacji, a następnie wybierz **OK**.

    ![Nowy projekt z istniejących źródeł, krok 1](media\create-project-existing\new-ai-project.png)

1. W oknie kreatora należy ustawić ścieżkę do istniejącego kodu, zdefiniować filtr dla typów plików i określ wszystkie ścieżki wyszukiwania, które Twój projekt wymaga, a następnie wybierz **OK**. Jeśli nie znasz wyszukiwania, jakie są ścieżki wypełniaj tego pola.


![Nowy projekt z istniejących źródeł, krok 2](media\create-project-existing\azurebatch-newproject.png)

> Sprawdź, czy istniejący kod jest częścią projektu usługi Azure Machine Learning, "**uczenia maszynowego Azure jest folder**" w celu zapewnienia pomyślnej konwersji istotne szczegóły konfiguracji usługi Azure Machine Learning, takie jak eksperymenty, które konto, które obszaru roboczego, kontekstów obliczeń do użycia i inne.

1. Aby ustawić pliku startowego, zlokalizuj plik w Eksploratorze rozwiązań, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako plik uruchamiania**.

8. W razie potrzeby, uruchom program naciskając klawisze Ctrl + F5 lub wybranie **Debuguj > Rozpocznij bez debugowanie**. 

> [!div class="nextstepaction"]
> [Samouczek: Praca z języka Python w programie Visual Studio](https://docs.microsoft.com/visualstudio/python/vs-tutorial-01-00)

## <a name="see-also"></a>Zobacz też

- [Tworzenie środowiska dla istniejących interpreter języka Python](https://docs.microsoft.com/visualstudio/python/python-environments#creating-an-environment-for-an-existing-interpreter)