---
title: "Opérations sur les programmes simultanés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbc40e4c-d5a1-4763-9683-09a744e5b656
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bd7aae5d90c85e913c0e65a20f1d03e81c526e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-concurrent-programs"></a>Opérations sur les programmes simultanés
Les programmes simultanés dans Oracle E-Business Suite sont signalées en tant qu’opérations dans [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  En même temps que les programmes simultanés spécifiques à une application Oracle, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] met également en évidence les trois opérations standards suivantes : Get_Status, Wait_For_Request et Submit_Request. Cela signifie que si une application Oracle a deux programmes simultanés, cinq opérations seront exposées : une pour chaque programme simultanée et trois pour les opérations standard.  
  
 Pour plus d’informations sur :  
  
-   Parcourir et rechercher des programmes simultanés, consultez [Parcourir, rechercher et obtenir des métadonnées pour des opérations Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
-   Comment appeler des programmes simultanés dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [appeler des programmes simultanés dans Oracle E-Business Suite à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md).  
  
> [!IMPORTANT]
>  Vous devez définir le contexte des applications pour les programmes simultanés dans [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avant de pouvoir effectuer des opérations sur les programmes simultanés. Il s’agit, car le contexte des applications paramètre facilite la sécurité des transactions dans Oracle E-Business Suite en définissant des préférences de l’utilisateur (telles que les paramètres de gestion, d’organisation et langage) et de contrôle d’accès pour un artefact. Pour plus d’informations sur le contexte des applications et comment le configurer, consultez le contexte d’Application défini[définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
 Les sections suivantes fournissent des informations sur les opérations exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour les programmes simultanés.  
  
##  <a name="Concurrent"></a>Opération de < Concurrent_Program_Name >  
 Comme mentionné précédemment, il y a autant d’opérations comme le nombre de programmes simultanés dans une application Oracle < Concurrent_Program_Name >. L’opération < Concurrent_Program_Name > prend cinq paramètres standards : trois de type complexe et deux de type simple.  
  
> [!NOTE]
>  Pour les programmes simultanés qui n’exposent pas leurs métadonnées, l’adaptateur Oracle E-Business expose 100 paramètres facultatifs pour chacun de ces programmes simultanés. Pour appeler ces programmes simultanés avec succès, l’utilisateur doit consultez la documentation d’Oracle E-Business Suite pour déterminer les paramètres pour un programme simultané qui nécessitent une valeur et puis de les spécifier. Est un exemple d’un tel programme simultané **importation du Journal** (nom réel : **GLLEZL**) dans le **comptabilité** application.  
  
 **Paramètres de type complexe**  
  
-   **SetOptions**: vous permet de définir des options pour le programme simultanée avant de soumettre la demande. SetOptions accepte les options suivantes en tant que paramètres :  
  
    -   **Implicite**: indique s’il faut afficher les demandes simultanées sous forme de demandes simultanées de l’utilisateur dans Oracle E-Business Suite. Vous pouvez spécifier une des quatre valeurs suivantes : **non**, **Oui**, **erreur** ou **avertissement**. Spécification de **non**entraîne les demandes à afficher sous forme de demandes simultanées de l’utilisateur dans Oracle E-Business Suite. Spécification de **Oui** implique que la demande peut être affichée qu’à partir de la forme de demandes simultanées privilégié de l’administrateur système. Spécification de **erreur** entraîne la demande à afficher sous forme de demandes simultanées de l’utilisateur uniquement en cas d’échec. Spécification de **avertissement** entraîne la demande pour l’afficher dans uniquement si l’utilisateur de demandes simultanées formulaire est un avertissement ou une erreur.  
  
    -   **Protégé**: indique si les demandes simultanées est protégé contre les mises à jour effectuées à l’aide de la forme de demandes simultanées dans Oracle E-Business Suite. Vous pouvez spécifier **Oui** (protégé) ou **non** (non protégé).  
  
    -   **Langue**: indique la langue prise en charge NLS (National Language). Si aucune valeur n’est spécifiée, la valeur par défaut est la langue actuelle.  
  
    -   **Territoire**: indique le secteur de langage. Si aucune valeur n’est spécifiée, la valeur par défaut est le secteur de langage actuelle.  
  
    -   **ContinueOnFail**: indique si l’envoi de demandes simultanées doit continuer ou lever une exception dans les cas **SetOptions** échoue. Vous pouvez spécifier **True** (Continuer) ou **False** (lèvent une exception).  
  
-   **SetPrintOptions**: permet de définir les options d’impression pour le programme simultanée avant de soumettre la demande. SetPrintOptions accepte les options suivantes en tant que paramètres :  
  
    -   **Imprimante**: indique le nom de l’imprimante où la sortie de demandes simultanées doit être envoyée. Vous ne pouvez modifier cette option d’impression s’il est déjà défini dans le formulaire de programmes simultanés dans Oracle E-Business Suite.  
  
    -   **Style**: indique le style d’impression pour imprimer la sortie de demandes simultanées. Par exemple, vous pouvez spécifier l’orientation (**paysage** ou **Portrait**). Si le style d’impression est déjà défini dans le formulaire de programmes simultanés dans Oracle E-Business Suite et le **Style requis** case à cocher est activée, vous ne pouvez pas substituer cette option d’impression.  
  
    -   **Copies**: indique le nombre de copies à imprimer de la sortie de demandes simultanées.  
  
    -   **SaveOutput**: indique s’il faut ou non enregistrer le fichier de sortie. Vous pouvez spécifier **Oui** ou **non**.  
  
    -   **PrintTogether**: Applicable uniquement pour les requêtes qui contiennent des sous-requêtes. Indique comment la sortie de sous-requêtes est imprimée. Si vous spécifiez **Y**, la sortie de sous-requêtes est imprimée uniquement une fois toutes les sous-requêtes ne sont terminés. Si vous spécifiez **N**, le résultat de chaque requête secondaire est imprimé tel qu’il se termine.  
  
    -   **ContinueOnFail**: indique si l’envoi de demandes simultanées doit continuer ou lever une exception dans les cas **SetPrintOptions** échoue. Vous pouvez spécifier **True** (Continuer) ou **False** (lèvent une exception).  
  
-   **SetRepeatOptions**: vous permet de définir les options de répétitions du programme simultanées avant de soumettre la demande. **SetRepeatOptions** accepte les options suivantes en tant que paramètres :  
  
    -   **RepeatTime**: indique l’heure du jour à répéter les demandes simultanées.  
  
    -   **RepeatInterval**: ce paramètre est applicable uniquement lorsque **RepeatTime** a la valeur NULL. Indique l’intervalle entre les nouvelles soumissions de la demande. Utilisez cette option avec **RepeatUnit** pour spécifier le délai entre nouvelles soumissions.  
  
    -   **RepeatUnit**: ce paramètre est applicable uniquement lorsque **RepeatTime** a la valeur NULL. L’unité de temps utilisée en association avec **RepeatInterval** pour spécifier le délai entre nouvelles soumissions de la demande. Vous pouvez spécifier **Minutes**, **heures**, **jours** ou **mois**.  
  
    -   **RepeatType**: ce paramètre est applicable uniquement lorsque **RepeatTime** a la valeur NULL. Indique si l’intervalle de répétition est appliquée après la « start » d’une exécution de demandes simultanées ou « fin » d’une exécution de demandes simultanées.  
  
    -   **RepeatEndTime**: indique la date et l’heure pour arrêter le soumettre à nouveau les demandes simultanées.  
  
    -   **ContinueOnFail**: indique si l’envoi de demandes simultanées doit continuer ou lever une exception dans les cas **SetRepeatOptions**. Vous pouvez spécifier **True** (Continuer) ou **False** (lèvent une exception).  
  
 **Paramètres de Type simple**  
  
-   **Description**: Description de la demande simultanée.  
  
-   **StartTime**: indique l’heure à laquelle les demandes simultanées doit démarrer en cours d’exécution.  
  
## <a name="getstatus-operation"></a>Get_Status opération  
 L’opération standard, Get_Status, retourne la phase/état de la demande et le message d’achèvement d’un programme simultané. Cette opération prend l’ID de demande d’un programme simultané (**RequestID**) en tant qu’entrée, puis retourne les informations suivantes :  
  
-   **Phase**: la phase de demande conviviale à partir de FND_LOOKUPS.  
  
-   **État**: l’état de la demande conviviale à partir de FND_LOOKUPS.  
  
-   **DevPhase**: la phase de demande sous forme de chaîne qui peut être utilisé pour les comparaisons de logique de programme.  
  
-   **DevStatus**: le statut de la demande sous forme de chaîne qui peut être utilisé pour les comparaisons de logique de programme.  
  
-   **Message**: le message d’achèvement si la demande est terminée.  
  
## <a name="waitforrequest-operation"></a>Opération de Wait_For_Request  
 L’opération standard, Wait_For_Request, attend la fin de la demande et retourne la phase/état de la demande et le message d’achèvement. Cette opération prend l’ID de demande d’un programme simultané (**RequestID**), le nombre de secondes d’attente entre les vérifications (**intervalle**) et la durée maximale en secondes d’attente (fin) de la demande **MaxWait**) en tant que paramètres d’entrée, puis retourne les mêmes informations que l’opération Get_Status.  
  
## <a name="submitrequest-operation"></a>Opération de Submit_Request  
 L’opération standard, Submit_Request, soumet une demande simultanée pour le traitement par un gestionnaire simultané. Si la demande se termine correctement, cette opération retourne l’ID de demandes simultanées. Sinon, elle retourne « 0 ».  
  
 L’opération Submit_Request prend six paramètres standards : trois de type simple de type complexe. En dehors de ces paramètres, il prend également les arguments du programme simultané comme un tableau de chaînes.  
  
 **Paramètres de type complexe**  
  
 L’opération Submit_Request **SetOptions**, **SetPrintOptions**, et **SetRepeatOptions** en tant que paramètres d’entrée. Pour plus d’informations sur ces paramètres, consultez [ &lt;Concurrent_Program_Name&gt; opération](#Concurrent) plus haut dans cette section.  
  
 **Paramètres de type simple**  
  
-   **Programme**: nom court du programme simultané pour laquelle la demande doit être soumise.  
  
-   **Description**: Description de la demande simultanée.  
  
-   **StartTime**: l’heure à laquelle les demandes simultanées doit démarrer en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)