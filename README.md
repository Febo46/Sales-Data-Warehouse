Data Source IMDB:
https://developer.imdb.com/non-commercial-datasets/

Creazione SQL server locale per funzioni di dwh.
Il dwh sarà formato da un livello bronzo in cui ci saranno i raw dataset di imdb, 
un livello argento con una pulizia e uno slicing del dataset

Architettura a Medaglione
  Livello Bronzo:
  Caricamento delle 7 tabelle raw statiche attraverso dei bulk insert da cartella in locale

BULK INSERT nome_tabella
FROM 'C:\imdb\nome_file.tsv'
WITH
(
    FIRSTROW = 2,
    FIELDTERMINATOR = '\t',
    ROWTERMINATOR = '0x0A',
    CODEPAGE = '65001',
    TABLOCK
);

   Livello Argento:
