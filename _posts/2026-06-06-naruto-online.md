---
layout: single
title: Naruto
date: 2026-06-06
author: esteve
tags: [shows]
---

La Laia feia mesos que em comentava que hauríem de veure Naruto, jo tenia al cap que era una sèrie molt llarga i d'entrada ho vam posposar. Però un cop havíem acabat Avatar (the Last Airbender) ens vam quedar amb mono de veure un anime (Avatar no és un anime, es veu) i vam decidir posar-nos-hi.

El volíem veure en català, i vam veure que l'única opció que tenia els drets en streaming era AnimeBox. L'aplicació deixa alguna cosa a desitjar però, com que no teníem alternativa (a TV3 encara no estaven pujats), ho vem veure des d'allà. Vam acabar Naruto, i ens va agradar tant que vam decidir començar Naruto Shippuden.

La primera temporada perfecte, però la segona no estava en català, i no ens posàvem d'acord en quin idioma seguir veient-lo. Vam arribar a l'acord que ho faríem en anglès i amb subtítols en anglès perquè la Laia pogués practicar, només hi havia un problema: aquesta opció no estava disponible a cap streaming des d'Espanya ni tampoc en altres opcions menys legals.

Després d'uns quants dies donant-li voltes vaig arribar a la solució, em descarregaria Naruto doblat a l'anglès i generaria jo mateix els subtítols. Per passos:

1. Descarregar Naruto en anglès, via BitTorrent
2. Transcriure els capítols utilitzant Whisper

    ```console
    cd "/home/red/naruto-shippuden"

    for video in *.mkv; do
        [ -e "$video" ] || continue
        srt="${video%.*}.srt"
        if [ -f "$srt" ]; then
            echo "Skipping $video (Found .srt file)"
            continue
        fi
        echo "Transcribing: $video"
        whisper "$video" --model medium --language English --task transcribe --output_format srt
    done
    ```

    ⚠️ Aquest script tardava 30 min aprox. per cada capítol! Així que vam deixar l'ordinador treballant durant la nit i mentre jugàvem al Rummikub per supervisar-lo.

    ![]({{site.baseurl}}/assets/images/posts/2026-06-06-naruto/transcribing.png)


3. Per poder-lo veure des de la televisió vam utilitzar Jellyfin. Després de barallar-me uns minuts amb els permisos i instal·lar l'aplicació corresponent ja estàvem molt feliços sopant a la televisió mirant Naruto. Hem vist que a vegades els subtitols passen més de pressa del que parlen però de moment ho tolerarem a falta d'una alternativa millor.