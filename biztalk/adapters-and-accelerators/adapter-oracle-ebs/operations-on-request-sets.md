---
title: "Opérations sur des ensembles de demande | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0537354d-821e-4cf9-a4d1-f4e7d1643df9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8051a94df28df4090f78287070c5143e6f866ed7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-request-sets"></a>Opérations sur des ensembles de demande
Une demande de définir dans Oracle E-Business Suite est un ensemble de rapports et des programmes simultanés sont organisés en plusieurs étapes. Vous pouvez utiliser une demande unique est configurée pour exécuter un ensemble de rapports et des programmes simultanés. Demander des jeux sont divisées en une ou plusieurs étapes, et chaque étape contient un ensemble de rapports et des programmes simultanés. Ces étapes sont liés entre eux, et l’ordre de l’exécution de chaque étape est défini. Pour plus d’informations spécifiques à Oracle sur les jeux de demande, accédez à [http://go.microsoft.com/fwlink/p/?LinkId=129539](http://go.microsoft.com/fwlink/p/?LinkId=129539).  
  
 [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]vous permet d’exécuter la demande définit dans Oracle E-Business Suite. La demande définit est exposée en tant qu’opérations dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Dans la mesure où un ensemble de la demande contient un ensemble de programmes simultanés, ces programmes simultanés sont les paramètres d’entrée pour une demande d’opération. En même temps que les programmes simultanés, l’opération de définition de requête accepte quatre paramètres de type complexe et un paramètre de type simple en tant qu’entrée.  
  
> [!IMPORTANT]
>  Vous devez définir le contexte des applications pour la demande définit [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avant de pouvoir effectuer des opérations sur les ensembles de requêtes. Il s’agit, car le contexte des applications paramètre facilite la sécurité des transactions dans Oracle E-Business Suite en définissant des préférences de l’utilisateur (telles que les paramètres de gestion, d’organisation et langage) et de contrôle d’accès pour un artefact. Pour plus d’informations sur le contexte des applications et comment le configurer, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## <a name="complex-type-parameters"></a>Paramètres de type complexe
  
-   **SetRelClassOptions**: permet de définir les options de planification pour l’ensemble de la demande. Si SetRelClassOptions et SetRepeatOptions sont définies puis SetRelClassOptions est prioritaire. SetRelClassOptions accepte les options suivantes en tant que paramètres :  
  
    -   **Application**: indique le nom court de l’application associée à l’ensemble de la demande.  
  
    -   **ClassName**: indique le nom de la classe associée à l’ensemble de la demande.  
  
    -   **CanceOrHold**: indique l’indicateur d’annuler ou de blocage.  
  
    -   **StaleDate**: indique la date ou après laquelle cet ensemble de la demande sera annulée si l’ensemble de la demande n’a pas encore exécuté.  
  
    -   **ContinueOnFail**: indique si l’envoi de la demande set doit continuer ou lever une exception en cas d’échec de SetRelClassOptions. Vous pouvez spécifier « True » (Continuer) ou « False » (lève une exception).  
  
-   **SetPrintOptions**: permet de définir les options d’impression pour l’ensemble de la demande. SetPrintOptions accepte les options suivantes en tant que paramètres :  
  
    -   **Imprimante**: indique le nom de l’imprimante où la demande de définir la sortie doit être envoyée.  
  
    -   **Style**: indique le style d’impression pour imprimer la demande de définir la sortie. Par exemple, vous pouvez spécifier l’orientation (« Paysage » ou « Portrait »).  
  
    -   **Copies**: indique le nombre de copies de la demande de définir la sortie à imprimer.  
  
    -   **SaveOutput**: indique s’il faut ou non enregistrer le fichier de sortie. Vous pouvez spécifier « True » ou « False ».  
  
    -   **PrintTogether**: Applicable uniquement pour les sous-requêtes. Indique comment la sortie de sous-requêtes est imprimée. Si vous spécifiez « Y », la sortie de sous-requêtes est imprimée uniquement une fois toutes les sous-requêtes ne sont terminés. Si vous spécifiez « N », le résultat de chaque requête secondaire est imprimé tel qu’il se termine.  
  
    -   **ContinueOnFail**: indique si l’envoi de la demande set doit continuer ou lever une exception en cas d’échec de SetPrintOptions. Vous pouvez spécifier « True » (Continuer) ou « False » (lève une exception).  
  
-   **SetRepeatOptions**: vous permet de définir les options de répétitions de l’ensemble de la demande. SetRepeatOptions accepte les options suivantes en tant que paramètres :  
  
    -   **RepeatTime**: indique l’heure du jour à répéter l’ensemble de la demande.  
  
    -   **RepeatInterval**: ce paramètre est applicable uniquement lorsque **RepeatTime** a la valeur NULL. Indique l’intervalle entre les nouvelles soumissions de la demande. Utilisez cette option avec **RepeatUnit** pour spécifier le délai entre nouvelles soumissions.  
  
    -   **RepeatUnit**: ce paramètre est applicable uniquement lorsque **RepeatTime** a la valeur NULL. L’unité de temps utilisée en association avec **RepeatInterval** pour spécifier le délai entre nouvelles soumissions de la demande. Vous pouvez spécifier « Minutes », « Heures », « Days » ou « Mois ».  
  
    -   **RepeatType**: ce paramètre est applicable uniquement lorsque **RepeatTime** a la valeur NULL. Indique si l’intervalle de répétition est appliquée après la « start » d’une précédente demande l’exécution ou après l’exécution du jeu de « fin » d’une demande précédente.  
  
    -   **RepeatEndTime**: indique la date et l’heure pour arrêter le soumettre à nouveau l’ensemble de la demande.  
  
    -   **ContinueOnFail**: indique si l’envoi de la demande set doit continuer ou lever une exception en cas d’échec de SetRepeatOptions. Vous pouvez spécifier « True » (Continuer) ou « False » (lève une exception).  
  
-   **SetNlsOptions**: vous permet de définir les options NLS pour l’ensemble de la demande. SetNlsOptions accepte les options suivantes en tant que paramètres :  
  
    -   **Langue**: indique la langue NLS.  
  
    -   **Langue**: indique le secteur de langage.  
  
    -   **ContinueOnFail**: indique si l’envoi de la demande set doit continuer ou lever une exception en cas d’échec de SetNlsOptions. Vous pouvez spécifier « True » (Continuer) ou « False » (lève une exception).  
  
## <a name="simple-type-parameter"></a>Paramètre de type simple
  
 **StartTime**: indique l’heure à laquelle l’ensemble de la demande doit démarrer en cours d’exécution.  
  
 Si la valeur de la demande termine correctement, un ID est retourné de demandes simultanées. Sinon, « 0 » est retournée.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)