---
title: Planification pour le portail BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, security
- BAM portal, prerequisites
- BAM portal, deploying
- developing, BAM portal
- planning, BAM portal
- BAM portal, planning
- BAM portal, developing
- deploying, BAM portal
- security, BAM portal
ms.assetid: 8a8bd331-c5a8-4d8b-9e93-96e6cd581a1d
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85f7291d56d662a8e3a9d46308d6b16ca2a1cafc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-the-bam-portal"></a>Planification du portail BAM
Cette rubrique traite des étapes que vous devrez envisager lors de la planification du déploiement de votre portail BAM.  
  
## <a name="prerequisites"></a>Conditions préalables  
 **Configuration système requise**. En plus de la configuration système requise pour BizTalk Server, vous devez installer les logiciels suivants afin d’installer le portail BAM :  
  
-   Internet Information Services (IIS)  
  
-   Microsoft Office Excel  
  
-   Microsoft Internet Explorer  
  
-   Microsoft .NET Framework  
  
-   Microsoft XML Core Services (MSXML) 6.0  
  
-   Microsoft Data Access Components (MDAC) 2.7  
  
## <a name="configuration-planning"></a>Planification de configuration  
 **Migration à partir de versions précédentes de BizTalk Server**. Une fois la migration depuis des versions précédentes de BizTalk Server terminée, les installations des pages existantes dans le portail BAM ne seront peut-être plus fonctionnelles. Pour que le portail BAM fonctionne correctement, consultez les considérations et instructions sur BAM contenues dans le guide de mise à niveau de BizTalk Server.  
  
 **Bases de données**. prenez en compte les informations suivantes lorsque vous planifiez des bases de données :  
  
-   Vous devrez planifier des index de vos bases de données pour améliorer les performances. Les colonnes de date et d'heure requièrent généralement un index dans la dimension de progression. Les requêtes portant sur des dimensions de progression dépourvues d'index sont lentes et ralentiront les performances de la table d'importation principale BAM.  
  
-   Vous devrez vous demander si vous devez configurer l'analyse BAM sans alertes.  
  
 **SQL Server Notification Services**. SQL Server Notification Services ne prend pas en charge les adresses d'hôte local ou IP dans les noms permettant d'identifier les serveurs.  C'est le cas dans deux emplacements :  
  
1.  Pendant la configuration : si vous avez sélectionné l'analyse BAM et activé les alertes, le processus de configuration demandera un nom de serveur.  
  
2.  Lors de la modification du fichier .xml de configuration : si vous tentez de modifier le fichier .xml de configuration laissé par le processus de configuration afin de le réutiliser.  
  
 **Installation d’IIS**. Portail BAM s’exécute uniquement sur un mode 32 bits. Si vous installez IIS sur un ordinateur 64 bits, vous devez veiller à ce qu'ASP.NET 2.0 soit activé en mode 32 bits. Pour ce faire, ouvrez le Gestionnaire des services Internet, ouvrez **Pool d’applications**, sélectionnez le pool d’applications (BAMAppPool), puis cliquez sur **paramètres avancés**. Dans **Activer les applications 32 bits**, sélectionnez **True**. Pour plus d’informations, consultez le guide de mise à niveau de BizTalk Server.  
  
## <a name="deployment-planning"></a>Planification du déploiement  
 **Déploiement multiserveur**. votre déploiement de BizTalk Server s'étend-il sur un environnement à plusieurs ordinateurs ? Si votre portail BAM est configuré sur un autre serveur que votre base de données d'alertes, vous devez augmenter la valeur du délai d'attente des services de requête dans un environnement à plusieurs serveurs. Pour plus d’informations de configuration supplémentaires, consultez [personnaliser la Configuration du portail BAM](../core/customizing-the-bam-portal-configuration.md).  
  
-   **Déploiement multiculturel**. votre déploiement de BizTalk Server s'étend-il sur un environnement multiculturel ? Lorsque vous installez BizTalk Server, l'interface utilisateur est définie sur la langue de la version que vous avez installée et le portail BAM applique les paramètres culturels de l'utilisateur qui le configure. Pour modifier le fichier web.config du portail BAM pour refléter votre propre paramètre culturel, voir [personnaliser la Configuration du portail BAM](../core/customizing-the-bam-portal-configuration.md).  
  
 **Le déploiement du cluster**. effectuez-vous un déploiement dans un cluster d'équilibrage de la charge réseau ? Consultez [personnaliser la Configuration du portail BAM](../core/customizing-the-bam-portal-configuration.md) des informations de configuration supplémentaires.  
  
 **SSL**. déployez-vous le portail BAM sur une installation IIS utilisant SSL ? Consultez le [personnaliser la Configuration du portail BAM](../core/customizing-the-bam-portal-configuration.md) rubrique des informations de configuration supplémentaires.  
  
 Les utilisateurs créant des vues doivent avoir installé le complément BAM pour Excel.  
  
## <a name="permissions"></a>Permissions  
 **Gestionnaire BAM**. la commande add-account du gestionnaire BAM (bm.exe) n'octroie pas automatiquement à l'utilisateur ajouté des autorisations d'accès à la base de données. En effet, pour exécuter le Gestionnaire BAM, il suffit de disposer d'autorisations dbo. En conséquence, l'accès à des agrégations RTA à partir du portail BAM provoque l'échec du serveur SQL Server sauf si vous appartenez à certains groupes dans SQL Server (voir ci-dessous).  
  
 **Rôles SQL Server**. pour accorder à un utilisateur l'accès à une base de données, vous devez être membre du groupe securityadmin ou du groupe sysadmin.  
  
 Les membres de ces groupes peuvent accorder des autorisations d'accès en exécutant sp_grantdbaccess et sp_grantlogin.  
  
 Pour plus d’informations sur les rôles dans SQL Server, consultez « Rôles dans Architecture de SQL Server » à [http://go.microsoft.com/fwlink/?LinkId=56205](http://go.microsoft.com/fwlink/?LinkId=56205).  
  
## <a name="development-planning"></a>Planification du développement  
 **Chaînes de connexion pour des tableaux croisés dynamiques**. l'utilitaire de gestion de l'analyse BAM ne modifie pas toujours les chaînes de connexion pour les définitions du tableau croisé dynamique d'agrégation RTA durant le déploiement. C'est le cas quand le tableau croisé dynamique RTA possède des chaînes de connexion OLAP préexistantes qui ont été manuellement modifiées alors que la casse de la clé de valeur est incorrecte. Par exemple, dans cette ligne du fichier XML de définition BAM, la clé est RTARef et non pas la clé RtaRef attendue :  
  
 **\<PivotTableView CubeRef = RTARef de « POCube » = « POAmountByLocation »\>**  
  
 En conséquence, le tableau croisé dynamique est généré via le cube OLAP et non via le tableau croisé dynamique RTA.  
  
 **Les noms de champs**. lorsque vous développez une solution d'analyse, nous vous recommandons de choisir différentes conventions d'attribution de noms pour les noms de champ. L'analyse BAM ne nécessite pas de noms uniques entre la section de vue de la définition d'analyse BAM et le cube OLAP de l'agrégation.  Par conséquent, le sélecteur de colonne et la liste déroulante de sélection de champ du générateur de requête Recherche d'activité peuvent contenir deux champs portant le même nom. Cela peut entraîner des erreurs au moment de sélectionner les champs appropriés afin de les inclure dans les résultats.  
  
 Les ports BizTalk Server qui utilisent des pipelines de transfert ne sont pas en mesure de suivre les données à partir de la charge de message. Les pipelines de transfert n'évaluant pas les types de message dans les noms de schéma, tous les messages ont des schémas nuls.  
  
-   Étant donné que le modèle de suivi est mappé vers une paire de port et de schéma, toute tentative d'un pipeline de transfert de suivre les données de charge de message échoue.  
  
 **Noms des tableaux croisés dynamiques**: lors de la planification et le développement de l’utilisateur se produisent dans la tâche des agrégations du portail BAM, vous devez créiez des noms conviviaux pour les tableaux croisés dynamiques que vous créez dans Excel.  Pour personnaliser le nom d'un tableau croisé dynamique, cliquez avec le bouton droit sur ce dernier, puis sélectionnez les options de tableau dans le menu contextuel.  
  
 **Plages de dates**. Lors de la création de requêtes et instance des alertes à l’aide de la page recherche d’activité Gardez à l’esprit que se le @@DateFirst valeur dans vos requêtes SQL ne correspond pas à la valeur CultureInfo.CurrentCulture.DateTimeFormat.FirstDayOfWeek, puis les plages de valeurs affichées sur le page de recherche ne correspondre pas les limites de la semaine utilisés pour générer les agrégations.  
  
 Par exemple, si le premier jour de la semaine dans le serveur SQL Server est fixé sur le dimanche, la plage de dates de la seconde semaine de 2005 s'étendra du 02/01/2005 au 08/01/2005 et les agrégations dans le serveur SQL Server et dans OLAP affichées pour la semaine 2 seront basées sur cette plage de dates. Toutefois, si le portail BAM spécifie le samedi comme premier jour de la semaine, un utilisateur parcourant la semaine 2 de 2005 verra une plage de données allant du 08/01/2005 au 14/01/2005 dans la page de recherche. Par conséquent, la valeur renvoyée par la requête de recherche risque de ne pas correspondre à la valeur d'agrégation affichée dans le tableau croisé dynamique.  
  
 Pour obtenir le résultat désiré, ajustez la plage horaire dans la requête de manière à extraire la plage de dates souhaitées.  
  
 **Navigation distribuée**. Le composant de navigation distribuée du portail BAM permet aux utilisateurs de voir les relations d'activité au-delà des limites distantes. Lorsque vous développez des activités, prenez en compte les éléments suivants :  
  
-   Il pourra arriver que vous placiez dans une même vue des activités associées issues de bases de données d'importation principale BAM séparées. Il est possible que des activités portent le même nom mais figurent sur des serveurs distincts. C'est le cas par exemple si deux départements différents ont chacun une activité de bon de commande. Lorsque l'utilisateur du portail BAM sélectionnera Vue dans le volet Mes vues du portail, il verra apparaître les deux activités répertoriées sous chaque tâche.  
  
-   Si des utilisateurs utilisent des portails BAM sur des serveurs distincts afin de consulter les vues déployées, des références doivent être activées symétriquement pour que les deux expériences de portail, exécutée chacune par rapport à sa base de données d'importation principale BAM locale, soient identiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de la configuration du portail BAM](../core/customizing-the-bam-portal-configuration.md)