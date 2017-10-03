---
title: "À l’aide de plusieurs Continuations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a38087-71ee-40b3-a957-6a2653bd6435
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e27a73fae39a55f05650c08397616f3cbe4fa80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-multiple-continuations"></a>Utilisation de plusieurs continuations
L'utilisation de l'Éditeur de modèle de suivi dans des environnements dans lesquels il existe plusieurs activités vous demande de comprendre le scénario dans lequel ces activités sont suivies pour que vous puissiez mapper les ports de réception, les orchestrations et les ports d'envoi dans le bon ordre.  
  
 Dans un modèle de suivi, l'Éditeur de modèle de suivi évalue automatiquement le début et la fin de l'activité. L'activité démarre lors de la collecte des premières données et termine lors de la collecte des dernières.  
  
 Dans la plupart des cas, la création d'une seule continuation, comme une continuation entre deux orchestrations, est un processus simple pour les développeurs. L'Éditeur de modèle de suivi s'avère complexe dans le cas de continuations multiples. Un scénario de continuations multiples a lieu lorsqu'une activité BAM (Business Activity Monitoring) s'étend sur plusieurs ports de réception, orchestrations et ports d'envoi. Pour pouvoir collecter les données BAM dans un seul enregistrement, vous devez créer des continuations entre toutes les planifications BizTalk Server. Ce processus peut s'avérer compliqué lorsqu'il est réalisé via l'interface utilisateur de l'Éditeur de modèle de suivi.  
  
 Cette rubrique décrit comment créer des continuations simples et multiples dans différents scénarios.  
  
#### <a name="base-scenario-description---multiple-receive-ports-orchestrations-and-send-ports"></a>Description du scénario de base : ports de réception, orchestrations et ports d'envoi multiples  
 Ce scénario implique un serveur BizTalk disposant de plusieurs ports de réception, orchestrations et ports d'envoi. Une propriété de contexte interchangeID générique est utilisée pour lier les continuations. Vous pouvez utiliser n'importe quelle propriété de contexte, comme activityID ou tout autre identificateur unique. Le choix d'un contenu particulier n'est pas associé à l'étude de ce scénario.  
  
 Dans le cadre de ce scénario, l'étude de l'élément de données/l'étape majeure/le contexte-propriété-valeur suivis à partir de ces ports et orchestrations n'est pas traitée. Cette partie du mappage est propre à la logique d'entreprise. L'objectif est de capturer toutes les données BAM de tous les ports et orchestrations sur une seule ligne dans la table d'activité finale. Les différents modes de réception et de traitement d'un message par les orchestrations présentent des défis et solutions très intéressants.  
  
> [!NOTE]
>  Le scénario d'un port ou d'une orchestration peut être considéré comme un cas spécial du scénario des ports et orchestrations multiples.  
  
#### <a name="scenario-solution-1---one-receive-port-and-one-orchestration"></a>Solution du scénario 1 : un port de réception et une orchestration  
 Dans ce scénario, un message arrive sur exactement un seul des ports de réception et est traité par une seule orchestration.  
  
 Pour créer la continuation, procédez comme suit :  
  
1.  Créez une continuation dans l'arborescence d'activité de dossier du modèle de suivi.  
  
2.  Choisissez le schéma de propriété de contexte en cliquant sur le **Source d’événement sélectionnez** bouton, puis en cliquant sur le **sélectionner la propriété de contexte** élément de menu.  
  
3.  Recherchez le **propriété interchangeId** dans le **nom de propriété de contexte** liste et sélectionnez-le.  
  
4.  Dans le schéma de propriété, mappez interchangeID sur le dossier de continuation que vous venez de créer.  
  
5.  Cliquez avec le bouton droit sur le nouveau nœud interchangeID dans l'arborescence, puis sélectionnez les ports d'origine du mappage.  
  
6.  Dans le **sélectionner des Ports** boîte de dialogue qui s’affiche, sélectionnez toutes les **N** ports de réception.  
  
7.  Créez un dossier ContinuationID dans l'arborescence d'activité.  
  
8.  Ouvrez chaque orchestration en cliquant sur le **Source d’événement sélectionnez** bouton, puis en cliquant sur le **sélectionner une planification d’Orchestration** élément de menu. À partir de chaque orchestration, cliquez avec le bouton droit sur une forme de l'orchestration, puis mappez la propriété de contexte interchangeID au nouveau dossier continuationID.  
  
 Dans un déploiement contenant trois orchestrations, votre modèle de suivi ressemblerait à ceci :  
  
 ![L’éditeur plusieurs scénario 1](../core/media/4761d680-7218-4404-a636-06739f70f344.gif "4761d680-7218-4404-a636-06739f70f344")  
  
#### <a name="scenario-solution-2---one-receive-port-and-multiple-orchestrations"></a>Solution du scénario 2 : un port de réception et plusieurs orchestrations  
 Dans ce scénario, un message arrive sur exactement un seul des ports de réception et est traité par chaque orchestration. Ceci ce produit car le message est envoyé simultanément à chacune des orchestrations.  
  
 Dans ce cas, nous avons besoin d'une continuation et d'un continuationID pour chaque orchestration. Le processus de création des continuations serait similaire à la procédure décrite dans la solution du scénario 1. Pour un déploiement comportant trois orchestrations, votre modèle de suivi qui ressemble à ceci :  
  
 ![Scénario 2 de Continuations multiples de continuations](../core/media/3cebd82f-9192-4d52-84c7-584f24e8ecca.gif "3cebd82f-9192-4d52-84c7-584f24e8ecca")  
  
#### <a name="scenario-solution-3---content-based-routing"></a>Solution du scénario 3 : routage basé sur le contenu  
 Ce scénario définit une solution de routage basé sur le contenu. Un message arrive sur exactement un seul des ports de réception et est envoyé à un seul port d'envoi. Ce routage a lieu en fonction de la valeur de la propriété de contexte du message. Dans ce cas, une seule continuation est nécessaire. Le mappage ressemble à ceci :  
  
 ![Scénario de continuation CBR. ] (../core/media/4459a73d-515f-4d6d-a68f-b18eee072df8.gif "4459a73d-515f-4d6d-a68f-b18eee072df8")  
  
> [!NOTE]
>  Le mappage ci-dessus est également valable pour un message qui arrive sur exactement un seul des ports de réception et qui est envoyé à tous les ports d'envoi.  
  
#### <a name="scenario-solution-4---one-orchestration-multiple-send-ports"></a>Solution du scénario 4 : une orchestration, plusieurs ports d'envoi  
 Dans ce scénario, il existe plusieurs d’envoi. ports. Un message est traité par une seule des orchestrations, qui est déterminé par les règles de traitement et est envoyé à tous les ports d’envoi. Dans ce cas, une seule continuation est nécessaire. Le mappage ressemble à ceci :  
  
 ![Scénario de continuation 4](../core/media/3ab10b51-d306-4ad1-acb6-6731e23394ac.gif "3ab10b51-d306-4ad1-acb6-6731e23394ac")  
  
#### <a name="scenario-solution-5---sequential-orchestrations"></a>Solution du scénario 5 : orchestrations séquentielles  
 Dans ce scénario, un message est traité par chaque orchestration, une par une, dans l'ordre, puis est transmis à l'orchestration suivante via la continuation. Le mappage ressemble à ceci :  
  
 ![Scénario de continuation 5](../core/media/563cacee-104c-4f8a-9836-da90aecb7487.gif "563cacee-104c-4f8a-9836-da90aecb7487")  
  
### <a name="collecting-data-in-an-asynchronous-environment"></a>Collecte de données dans un environnement asynchrone  
 Lorsque vous configurez les continuations, la fonction BAM attend l'arrivée des données. Dans un environnement asynchrone, vous ne pouvez pas recevoir de réponse provenant d'un processus principal.  
  
 Si vous ne recevez pas les données de réponse, l'instance de l'activité attend indéfiniment. L'activité ne s'arrête jamais et les enregistrements restent dans les tables de la base de données d'importation principale BAM. Prenez le cas des transactions à long terme, où il n'est pas possible de connaître le moment d'arrivée des données. Il n'y a pas de délai d'expiration, puisque l'arrivée des données dépend de la logique ou des processus d'entreprise, après quoi l'activité est marquée comme étant terminée. Les données peuvent arriver le jour même, ou dans de rares cas, l'année suivante.  
  
 La solution est d'utiliser des activités connexes.  
  
 Séparez votre activité en deux activités distinctes. Liez les deux activités entre elles, et liez la réponse à l'activité initiale.  
  
 Pour plus d’informations sur les activités connexes, consultez [relations d’activité](../core/activity-relationships.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)