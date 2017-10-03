---
title: "L’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b3c92f-3062-413e-8d89-797f1c7ea7ab
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9003c89f7e1e3491ff343078936a9f22e6a41ef1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-activity-monitoring"></a>Analyse BAM (Business Activity Monitoring)
Dans le cadre de la surveillance et de l'évaluation des processus d'entreprise, les travailleurs de l'information doivent bénéficier d'une flexibilité accrue. Par exemple, un responsable des achats peut avoir besoin de voir combien de bons de commande sont approuvés et refusés quotidiennement, tandis qu'un responsable des ventes peut vouloir une mise à jour des commandes de produits toutes les heures. Pour répondre à ces différents besoins, une structure globale permettant d'assurer le suivi des événements associés à chacun des processus d'entreprise, telle que le composant BAM (Business Activity Monitoring) de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], est indispensable.  
  
 ![Diagramme de l’analyse BAM](../core/media/bam-diagram.gif "bam_diagram")  
  
 Comme l'illustre le schéma suivant, le composant BAM permet d'assurer le suivi des événements et des données produits par une application BizTalk. Ces informations sont accessibles via les services Web pouvant être appelés par SOAP, ou comme suit :  
  
-   Via Microsoft Excel ou d'autres clients de bureau, tels qu'un tableau de bord personnalisé.  
  
-   À l'aide d'un portail BAM (composant de BizTalk Server qui permet aux utilisateurs de l'entreprise d'examiner et de configurer les informations BAM). Ce dernier permet à un travailleur de l'information de sélectionner une instance spécifique d'un processus d'entreprise, puis de choisir une vue BAM spécifique dans celui-ci. Chaque vue offre une perspective différente, telle que la représentation graphique des tendances de ventes par produit ou des niveaux de stock actuels, ou d'autres indicateurs de performance clés. Les informations contenues dans ces vues peuvent être actualisées tous les jours, toutes les heures, ou plus fréquemment encore. À l'aide du portail BAM, un travailleur de l'information peut également définir des agrégations de données, comme le nombre de commandes satisfaites, annulées ou en cours, au cours de la dernière heure. Implémenté sous la forme d'un ensemble de pages ASP.NET, le portail BAM peut également être hébergé en tant que site Web au sein des services Windows SharePoint.  
  
-   Via SQL Server Notification Services, pour que les informations BAM soient transmises sous forme de notifications. Tandis que les deux premières options permettent aux travailleurs de l'information d'examiner les informations BAM, cette troisième option génère une notification lorsqu'un événement intéressant survient. À l'aide du gestionnaire d'alertes du portail BAM, un travailleur de l'information peut définir les alertes qui sont envoyées lorsqu'un événement spécifique survient. Par exemple, un utilisateur BAM peut choisir d'envoyer un message électronique à un gestionnaire particulier si plus de dix commandes sont annulées pour une journée, ou informer les commerciaux lorsqu'une commande est émise par un gros client.  
  
 Chaque vue BAM repose sur une ou plusieurs activités BAM. Une activité BAM représente un processus d'entreprise spécifique (gestion des bons de commande, expédition d'un produit, etc.) et inclut un jeu défini d'étapes majeures et de données d'entreprise. Par exemple, une activité de bon de commande peut inclure des étapes majeures telles que Approved (Approuvé), Denied (Refusé) et Delivered (Envoyé), avec les données d'entreprise Nom du produit et Produit.  
  
 Pour les travailleurs de l’accès à BAM via Excel, les activités BAM et les vues BAM peuvent être créés en utilisant un complément Excel. L’Assistant activité BAM pour ce complément permet de définir des activités, tandis que l’Assistant Vue BAM permet de définir des vues basées sur ces activités. En fait, l'Assistant Vue BAM aide un travailleur de l'information à créer un tableau croisé dynamique Excel standard à l'aide des informations associées à une ou plusieurs activités BAM. Les informations fournies par cette vue peuvent ensuite être affichées directement dans Excel, comme l'illustre le schéma ci-dessous.  
  
 ![](../core/media/understandingbts-12-bam2.gif "UnderstandingBTS_12_BAM2")  
  
 Dans cet exemple, deux graphiques Excel affichent des informations sur la progression des commandes et des ventes. En fonction de la complexité de la vue BAM, son créateur peut indiquer les utilisateurs autorisés à consulter les données qui y sont exposées. Il est donc possible qu'un responsable des achats puisse accéder à certaines données dans une vue au cours du processus de commande, mais pas ses assistants.  
  
 Si les travailleurs de l'information peuvent créer des vues et des activités BAM, celles-ci reposent sur les informations fournies par les orchestrations qu'elles surveillent. Par conséquent, les développeurs ont encore un rôle à jouer. À l'aide d'un outil nommé Éditeur de modèle de suivi (TPE), un développeur doit configurer une orchestration pour qu'elle fournisse les informations requises pour une activité BAM spécifique, et pour les vues BAM qui dépendent de celle-ci. Cet outil permet à un développeur d'associer de manière graphique les événements et les champs de message appropriés dans une orchestration avec les étapes majeures et les données commerciales dans une activité BAM. Le moteur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie par la suite ces valeurs d'événements et de champs de messages vers la base de données des suivis (voir la figure précédente), où le composant BAM peut y accéder. Les développeurs ne sont pas concernés par les activités et les vues BAM. Ces services orientés entreprise sont uniquement créés, mis à jour et utilisés par les travailleurs de l'information.  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'outil TPE peut également être utilisé pour spécifier la façon dont les pipelines génèrent les événements. En outre, BAM peut désormais accepter et afficher les événements générés par n'importe quel code utilisateur, qu'il soit créé ou non en tant qu'orchestration. Chaque application développée à l'aide de .NET Framework peut donc potentiellement être surveillée à l'aide du composant BAM de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Information Worker Technologies](../core/information-worker-technologies.md)