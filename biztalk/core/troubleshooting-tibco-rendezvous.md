---
title: Résoudre les problèmes de TIBCO Rendezvous | Documents Microsoft
description: Utiliser le suivi d’événements Windows pour troubl = esdhoot l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous dans BizTalk Server
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b7bc3ab-16fa-4e91-8730-9431473b2fb4
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18ae8d599b67a1a572021cae0ebc9bfc64992a9b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshoot-tibco-rendezvous"></a>Résoudre les problèmes de TIBCO Rendezvous
  
## <a name="use-event-tracing-for-windows"></a>Utiliser le suivi d’événements pour Windows
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous consigne des messages d'erreur, d'avertissement et d'informations dans l'Observateur d'événements Windows. Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d’événements pour Windows (ETW). Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages. Ce fichier au format binaire doit être converti pour être lu. Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.exe. Par exemple, l’application tracerpt.exe convertira la \*fichier .etl dans deux fichiers texte : summary.txt et dumpfile.csv.  
  
## <a name="etw-components"></a>Composants ETW  
 Le Suivi d'événements pour Windows comporte trois composants :  
  
-   **Application de contrôleur**: active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).  
  
     Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe. Cela permet de s’assurer que les appels BTATIBCO RendezvousTrace peuvent localiser tracelog.exe dans le système. Par défaut, BTATIBCO RendezvousTrace recherche le chemin d'accès actuel.  
  
> [!NOTE]
>  tracelog.exe est disponible dans le Kit de développement logiciel Microsoft (SDK) et est compatible avec les commandes fournies par l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous. Pour utiliser logman.exe, consultez la documentation de logman.  
  
-   **Application consommateur**: lit les événements enregistrés.  
  
     Pour que l'application consommateur puisse lire les événements dans le fichier .etl, l'outil Suivi d'événements pour Windows doit les vider dans ce fichier. Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.  
  
     Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, \<en temps réel\> = -rt.  
  
-   **Fournisseur**: fournit l’événement.  
  
     L'adaptateur BizTalk pour TIBCO Rendezvous inclut trois fournisseurs distincts, Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation). Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.  
  
 L'adaptateur BizTalk pour TIBCO Rendezvous inclut trois fournisseurs. Vous pouvez ainsi consigner différents types de messages :  
  
-   **Fournisseur de journalisation de récepteur**: le \<élément Trace\> commutateur est **-récepteur**.  
  
-   Utilisez **-récepteur** pour récupérer tous les messages du journal qui ont été reçus par l’adaptateur lors de l’exécution.  
  
-   **Fournisseur de journalisation de l’émetteur**: le \<élément Trace\> commutateur est **-émetteur**.  
  
     Utilisez **-émetteur** pour récupérer tous les messages du journal qui ont été transmis par l’adaptateur au moment de l’exécution.  
  
-   **Fournisseur de journalisation de gestion —**le \<élément Trace\> commutateur est **-gestion**.  
  
     Utilisez **-gestion**pour récupérer tous les messages du journal qui ont été générés pendant la navigation du système du serveur.  
  
## <a name="btatibcorvtrace-command"></a>Commande BTATIBCORVTrace  
 Pour utiliser ETW, exécutez l’adaptateur BizTalk pour commande TIBCO Rendezvous (btatibcbtatibcorvtrace.cmd). Utilisez-la comme suit :  
  
```  
BTATIBCORVTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTATIBCORVTrace <Trace element> -stop  
```  
  
 Où : **\<élément Trace\>** (obligatoire) est le type de fournisseur.  
  
 Les options associées sont les suivantes :  
  
-   **-transmitter**  
  
-   **-receiver**  
  
-   **-management**  
  
-   **-start, - stop**: activer ou désactiver le fournisseur.  
  
-   **-cir \<Mo\>**: taille et type de fichier. **-cir** est un fichier circulaire. **\<Mo\>**: taille en mégaoctets.  
  
-   **-seq \<Mo\>**: taille et type de fichier. **-seq** est un fichier séquentiel. **\<Mo\>**: taille en mégaoctets.  
  
-   **-rt**: définir le mode temps réel sur.  
  
-   **Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).  
  
 Par exemple :  
  
```  
BTATIBCORVTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCORVTrace -transmitter -stop  
```  
## <a name="see-more"></a>Voir plus d’informations
[Gérer les exceptions](../core/using-biztalk-server-exception-handling4.md)  
[Sécurité](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)  
[Architecture](../core/architecture-of-biztalk-adapter-for-tibco-rendezvous.md)