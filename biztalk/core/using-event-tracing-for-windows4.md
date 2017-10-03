---
title: "À l’aide du suivi d’événements pour Windows4 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- BTAJDEEnterpriseOneTrace command
- Event Tracing for Windows
ms.assetid: 5f07d317-5ae2-4d1e-a343-941f3079dc4b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c7614ae4f6470427a77815338767b04f07aaa73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-event-tracing-for-windows"></a>À l’aide d’événements de suivi pour Windows
L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne consigne des messages d'erreur, d'avertissement et d'informations dans l'Observateur d'événements Windows. Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d'événements pour Windows (ETW). Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages. Ce fichier au format binaire doit être converti pour être lu. Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.ex. L’application tracept.exe convertit le \*.etl dans deux fichiers texte : summary.txt et dumpfile.csv.  
  
## <a name="etw-components"></a>Composants ETW  
 Le Suivi d'événements pour Windows comporte trois composants :  
  
-   **Application de contrôleur**. active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).  
  
     Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe. Cela garantit que les appels BTAJDEEnterpriseOneTrace peuvent localiser tracelog.exe dans votre système. Par défaut, BTAJDEEnterpriseOneTrace recherche le chemin d'accès actuel.  
  
> [!NOTE]
>  tracelog.exe est disponible dans le Kit de développement logiciel (SDK) Microsoft et est compatible avec les commandes fournies par l'adaptateur BizTalk pour JD Edwards EnterpriseOne. Pour utiliser logman.exe, consultez la documentation de logman.  
  
-   **Application consommateur**. lit les événements enregistrés. Pour que l'application consommateur puisse lire les événements dans le fichier .etl, l'outil Suivi d'événements pour Windows doit les vider dans ce fichier. Normalement, cette opération est effectuée lorsque le contrôleur désactive le suivi.  
  
     Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel,  **\<en temps réel > = -rt**.  
  
-   **Fournisseur**. utilisé pour fournir l'événement. L'adaptateur BizTalk pour JD Edwards EnterpriseOne inclut trois fournisseurs distincts, Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation). Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.  
  
 L'adaptateur BizTalk pour JD Edwards EnterpriseOne inclut trois fournisseurs, ce qui permet de consigner plusieurs types de messages :  
  
-   **Fournisseur de journalisation de récepteur**: le \<Trace element > commutateur est **-récepteur**. Utilisez **-récepteur** pour récupérer tous les messages du journal qui ont été reçus par l’adaptateur au moment de l’exécution.  
  
-   **Fournisseur de journalisation de l’émetteur**: le \<Trace element > commutateur est **-émetteur**. Utilisez **-émetteur** pour récupérer tous les messages du journal qui ont été transmis par l’adaptateur au moment de l’exécution.  
  
-   **Fournisseur de journalisation de gestion**: le \<Trace element > commutateur est **-gestion** utilisez **-gestion** pour récupérer tous les messages du journal qui ont été générés pendant la navigation du système du serveur.  
  
### <a name="btajdeenterpriseonetrace-command"></a>Commande BTAJDEEnterpriseOneTrace  
 Pour utiliser ETW, exécutez l’adaptateur BizTalk pour JD Edwards EnterpriseOne commande, **BTAJDEEnterpriseOneTrace.cmd**. Utilisez-la comme suit :  
  
```  
BTAJDEEnterpriseOneTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTAJDEEnterpriseOneTrace <Trace element> -stop  
  
```  
  
 Où :  **\<Trace element >** (obligatoire) est le type de fournisseur.  
  
 Les options associées sont :  
  
-   **-émetteur**  
  
-   **-récepteur**  
  
-   **-gestion**  
  
-   **-start, - stop**: activer ou désactiver le fournisseur.  
  
-   **-cir \<Mo >**: taille et type de fichier. -cir signifie qu'il s'agit d'un fichier circulaire. \<Mo > : taille en mégaoctets.  
  
-   **-seq \<Mo >**: taille et type de fichier. -seq signifie qu'il s'agit d'un fichier séquentiel. \<Mo > : taille en mégaoctets.  
  
-   **-rt**: définir le mode temps réel sur.  
  
-   **Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).  
  
 Exemple :  
  
```  
BTAJDEEnterpriseOneTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEEnterpriseOneTrace -transmitter -stop  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md)