# Tydzień 2

1. Static Content
   1. Zasoby typu zdjęcia nie obciążają serwisów 
   2. Mogą być cache-owane blisko użytkowników końcowych
   3. Zmniejszone koszty na storage

    Usługi: **Azure CDN** - usługa dedykowana do tego typu rozwiązań.
    
2. CQRS
   1. Rozdzielenie operacji zapisu i odczyty. Z definicji operacji typu wrzucanie przedmiotów czy nawet samego składania ofert będzie wielokrotnie mniej niż przeglądania ofert.
   2. Możliwość wykonywania komend asynchronicznie co powinno przełożyć się na lepsze zarządzanie obciążeniem.
   3. Uproszczenie/dopasowanie operacji pod odczyt i zapis danych.
   4. Możliwość rozdzielenia storage-ów dla zapisu i odczytu, co dodatkowo wspiera możliwości niezależnego skalowania w zależności od obciążenia danymi typami operacji.
   5. Przy jego okazji można wykorzystać również wzorzec Materialized View dla jeszcze większego uproszczenia odczytu danych.
   
   Usługi: Koniecznie baza danych, ale jako, że nie miałem do czynienia z e-commerce a i z samymi bazami nie wielkie, ciężko mi jest wskazać która SQL czy NoSQL byłaby najlepsza do tego typu rozwiązania. Tu na pewno pod rozważania wziąłbym **CosmosDB** lub **Azure SQL Database**. Obie są w pełni zarządzane, dają duże możliwości skalowania jak i sporą gwarancję na poziomie SLA.

3. Throttling i Autoscaling
   1. Ograniczenie zapytań przy nagłym ich wzroście, w szczególności dla najbardziej obciążających "użytkowników" co pozwoli utrzymać świadczenie usług dla pozostałych.
   2. Sama throttlowanie na nie wiele się zda bez autoscalingu, ale pozwoli jednak zyskać czas na postawienie dodatkowych zasobów.

    Usługi: **API Management** - przydatne nie tylko w samych throttlingu dla którego można ustawiać reguły, ale również w zabezpieczeniu dostępu do konkretnych zasobów poszczególnym użytkonikom aplikacji. Przyda się też w zarządzaniu wszystkimi API jakie aplikacja będzie dostarczała.
