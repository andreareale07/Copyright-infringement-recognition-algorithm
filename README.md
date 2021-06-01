# Copyright-infringement-recognition-algorithm

Tecnologie utilizzate:
- Python
- Nozioni di computer vision
- SIFT, SURF
- Jupyter 

L’obiettivo del software sviluppato è di preservare il copyright di video caricati in un’ipotetica
piattaforma. Quando l’utente richiede l’upload di un video, il gestore dovrebbe effettuare dei
controlli sul contenuto in possesso dall’utente. Per preservare i diritti d’autore di fronte al
numero elevato di contenuti multimediali nel web, è necessaria una collaborazione tra
autore e piattaforma di video sharing. L’autore, può fornire un supporto attivo o passivo. Il
supporto attivo consiste nell’inserire delle informazioni nascoste all’interno del video
originale (watermarking e/o altri metodi steganografici), in modo da risalire all’autore. In
questo caso, il proprietario deve fornire anche gli strumenti di estrazione della firma
nascosta che verranno utilizzati dalla piattaforma per preservare i diritti d’autore. Il supporto
passivo invece consiste nel delegare il gestore della piattaforma all’estrazione della firma,
l’autore deve limitarsi a fornire il video originale.
Il software sviluppato si posiziona in quest’ultimo caso, l’autore fornisce il video originale dal
quale verrà calcolata la firma tramite due tipi di keypoint: surf e sift.
Con il medesimo algoritmo, verrà generata la firma del video che l’utente vuole caricare sulla
piattaforma, che da ora in poi chiameremo video query.
A questo punto bisognerà confrontare le firme del video originale e del video query.La
metodologia di confronto è il brute force, ogni frame del video originale verrà confrontato con
ogni frame del video query. Se un frame combacia con un altro, si passerà al successivo
frame originale, evitando di confrontarli tutti migliorando il tempo computazionale, a discapito
però della perdita dell’informazione del migliore match.
Per ridurre la complessità computazionale, si sono adottate varie tecniche: confronto locale,
maschera e skip tramite voting.
Nel confronto locale, in caso di match, il frame originale successivo, verrà confrontato con
un intorno locale a partire dall’indice dell’ultimo match. In questo modo se il match
corrisponde con un allineamento temporale del video, i frame successivi combaceranno con
i frame locali, risparmiando tempo computazionale.
Per limitare il numero di confronti totale tra descrittori, si è pensato di limitare il numero di
keypoint. Per filtrare il numero totale di descrittori per ogni frame, si applica una maschera
per si posiziona nella parte centrale del frame. La percentuale di frame che la maschera
seleziona è di default il 30%, ma risulta essere un parametro modificabile.
Selezionando quindi solo una porzione di frame, si limita il numero di descrittori trovati su
quest’ultimo.
La maschera a sua volta è stata divisa in 3 sezioni, in ognuna di queste verranno calcolati i
descrittori. Per limitare il numero di confronti totali tra frame, si è implementato un sistema di
voti per skippare frame che consideriamo “troppo diversi”. Se il rapporto tra il numero di
descrittori di ogni sezione supera un certo intorno, consideriamo i frame differenti, e non si
procede al confronto tra keypoint.

I file video presenti vengono utilizzati al solo e unico scopo di fornire dei test e degli esempi di funzionamento del software, pertanto non si intende perseguire alcuna violazione di copyright o di diritti, non vi è alcun tentativo di incitamento alla riproduzione non autorizzata.
