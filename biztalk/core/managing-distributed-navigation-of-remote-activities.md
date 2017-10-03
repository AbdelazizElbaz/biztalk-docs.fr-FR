---
title: "Gestion de la Navigation distribuée des activités distantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cf6e0c2-ea72-4621-9ca7-fa43e404ec46
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb21de97643d864a47d93a2ddd31e08bdd30532
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-distributed-navigation-of-remote-activities"></a>Gestion de la navigation distribuée des activités distantes
La navigation distribuée des activités distantes est le processus par lequel un utilisateur des activités navigue vers les activités qui existent dans des bases de données BAM distinctes et affiche ces activités. Lorsque vous configurez l'infrastructure BAM pour permettre la navigation distribuée, l'activité distante est accessible à l'utilisateur des activités dans le portail BAM. Lorsque l'utilisateur clique sur l'activité, celle-ci est ouverte sur le portail BAM distant. À ce stade, l'utilisateur a été transféré de manière transparente et fluide vers le portail BAM distant et peut naviguer vers la recherche d'activité, les agrégations et la gestion des alertes de l'activité comme si l'activité existait dans son magasin de données de base.  
  
## <a name="why-use-distributed-navigation-of-activities-and-documents"></a>Pourquoi utiliser la navigation distribuée des activités et des documents ?  
 La navigation distribuée permet aux organisations de garder le contrôle des bases de données BAM départements sans avoir à s’accorder sur un emplacement unique pour les activités. Cela permet également pour améliorer les performances de vos bases de données BAM en distribuant la charge système des activités dans l’ensemble de votre environnement.  
  
 La figure suivante illustre un scénario dans lequel la navigation distribuée répond au besoin de l'utilisateur des activités d'accéder aisément aux activités gérées par des services distincts de l'entreprise. Les administrateurs de ces services conservent le contrôle des processus d'entreprise propres à leur service.  
  
 Ce scénario implique les participants suivants :  
  
-   un administrateur qui détient l'infrastructure du service commercial. L'administrateur est uniquement responsable de la disponibilité et de la sécurité des données du service ;  
  
-   un administrateur qui détient l'infrastructure du service d'expédition. Cet administrateur est chargé de répondre aux besoins du service commercial ;  
  
-   un utilisateur des activités du service commercial. L'utilisateur des activités voit les sous-ensembles des données commerciales incluses dans les vues auxquelles il a été ajouté. Les vues sont créées par l'administrateur, qui accorde à l'utilisateur des activités l'accès à ces vues. La vue principale d'entreprise de l'utilisateur des activités est l'activité de bon de commande à laquelle il participe. Cet utilisateur est configuré pour afficher la page d'accueil du portail BAM géré par l'administrateur du service commercial.  
  
 **À l’aide de la Navigation distribuée dans BAM**  
  
 ![Scénario de navigation distribuée. ] (../core/media/bcd-distrbuted-nav-scenario.gif "bcd_distrbuted_nav_scenario")  
  
 Les administrateurs souhaitent configurer leurs serveurs de sorte qu'ils soient aussi indépendants que possible, comme suit :  
  
-   l'administrateur du service commercial ne souhaite pas que l'acceptation des commandes s'arrête ou que la fonctionnalité de requête de ses utilisateurs d'activités soit affectée si l'infrastructure du service d'expédition est en panne ;  
  
-   l'administrateur du service d'expédition ne souhaite pas que son service soit affecté par des problèmes de performances dans le service commercial. Il souhaite que ses utilisateurs d'activités puissent suivre l'avancée des expéditions, même si le service commercial n'est pas opérationnel.  
  
 L'objectif de la navigation distribuée est de permettre à l'utilisateur final du processus d'entreprise d'accéder à chaque vue pour laquelle il dispose d'autorisations.  
  
 Par exemple, les vues A et B sont définies dans la base de données des ventes. La vue C est définie pour le service d'expédition. L'utilisateur des activités est autorisé à afficher toutes ces vues et à accéder au portail BAM spécifique au service commercial. Pour autoriser l’utilisateur d’entreprise voir les vues A, B et C dans les **Mes vues** frame du portail, établissez au moins une approbation à sens unique à partir de la base de données de ventes pour la base de données de l’envoi de journaux.  
  
> [!NOTE]
>  Les autorisations qui indiquent quelle catégorie d'utilisateurs d'activités peut voir quelles données sont définies par l'utilisateur des activités avec pouvoir, tel qu'un gestionnaire ou un analyste. Les administrateurs ajoutent uniquement des utilisateurs à des groupes ou des vues BAM existantes.  
  
 La navigation distribuée des activités BAM permet également à l'utilisateur de voir les relations d'activité distribuée et d'accéder à ces relations. Lorsque des instances d'activités existent sur deux bases de données BAM différentes ayant été associées l'une à l'autre par la navigation distribuée, l'activité associée distante est affichée en tant qu'activité associée dans les détails d'activité de l'instance de l'activité locale. Le fait de cliquer sur l'activité associée ouvre la page des détails d'activité de l'activité sur le portail distant. Pour plus d’informations sur les activités associées de la page de résultats de recherche activité dans le portail BAM, un, consultez [des activités connexes](../core/related-activities.md).  
  
> [!IMPORTANT]
>  Pour que les utilisateurs de chaque ordinateur puissent voir les activités connexes situées dans les différentes bases de données de l'analyse BAM, vous devez activer la navigation distribuée bidirectionnelle entre toutes les bases de données BAM.  
  
 Si vous activez la navigation distribuée unidirectionnelle entre deux bases de données d'importation principales lorsque vous configurez la navigation distribuée, les utilisateurs auront une expérience asymétrique pendant la navigation.  
  
 L'expérience de l'utilisateur sera telle que l'utilisateur verra les différentes activités. Cependant, lorsqu'il parcourra les données de niveau d'instance, la section dans laquelle les instances associées sont affichées sera vide. Pour résoudre ce problème, vous devez reconfigurer le chemin de navigation distribuée sur le serveur de portail BAM de base de l'utilisateur.  
  
 Observez par exemple le scénario suivant :  
  
-   Sur l'ordinateur 1, vous disposez d'une activité nommée Purchase Order et d'une vue nommée SalesManager.  
  
-   Sur l'ordinateur 2, vous disposez d'une activité nommée Shipping Order et d'une vue nommée SalesManager.  
  
-   Vous ajoutez une activité nommée PO_1 à Purchase Order sur l'ordinateur 1.  
  
-   Vous ajoutez une activité nommée SO_1 à Shipping Order sur l'ordinateur 2.  
  
-   Sur l'ordinateur 2, vous ajoutez la relation, SO_1, à l'activité PurchaseOrder PO_1 sur Shipping Order.  
  
-   Lorsqu'un utilisateur parcourt l'activité SO_1 à partir de l'ordinateur 1, l'activité SO_1 est détectable.  
  
-   Si l'utilisateur parcourt l'activité SO_1 sur l'ordinateur 2, l'activité PO_1 n'est pas visible.  
  
 Pour corriger cela, vous devez ajouter la relation sur l'ordinateur 1.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment configurer la Navigation entre les activités distribuées](../core/how-to-configure-navigation-between-distributed-activities.md)  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion BAM](../core/managing-bam.md)