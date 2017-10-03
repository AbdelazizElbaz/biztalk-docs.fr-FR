---
title: Alertes dans le portail BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, alerts
- alerts, summaries
- subscriptions, alerts
- alerts, details
- Alert Management page [BAM portal]
- alerts, subscriptions
ms.assetid: 715a4187-aafa-46be-8b00-8eaba2e569e5
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb94ad682eafec00d1947e795887a16dafb9d11f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="alerts-in-the-bam-portal"></a>Fonctionnement des alertes dans le portail BAM
Les alertes vous permettent de définir des événements importants pour votre processus d'entreprise (indicateurs de performance clés, par exemple) et de les communiquer à des utilisateurs en temps réel. Les utilisateurs s'abonnent à des alertes et reçoivent les notifications concernant les événements commerciaux contrôlés par cette alerte.  
  
 Par exemple, lorsqu'un événement clé a lieu, plutôt que d'attendre la publication du rapport correspondant pour en prendre connaissance, vous pouvez être informés par messagerie ou au moyen d'un fichier enregistré à un emplacement d'où il peut être extrait de façon programmée avant de vous être remis de différentes manières.  
  
## <a name="types-of-alerts-and-how-they-are-delivered"></a>Types des alertes et manières dont elles sont remises  
 Il existe deux types d'alertes : les alertes d'agrégation et les alertes d'instance. Une alerte d'agrégation vous permet de spécifier des données limites dans un laps de temps défini tandis qu'une alerte d'instance s'appuie sur des points de données spécifiques recevables.  
  
 La transmission des alertes se fait de deux façons différentes. Elle peuvent être remises aux abonnés par messagerie ou écrites à un emplacement spécifié par le système sous forme de fichier. Une alerte transmise par courrier électronique comporte une ligne d'objet correspondant au nom de l'alerte. Le corps du message comprend le texte défini pour l'alerte concernée ainsi qu'un lien vers la page des résultats associés à l'alerte dans le portail BAM.  
  
## <a name="the-alert-management-page"></a>Page Gestion des alertes  
 La page Gestion des alertes est divisée selon les trois zones suivantes :  
  
### <a name="alert-summary"></a>Résumé des alertes  
 Le **résumé des alertes** zone du cadre contenu gestion des alertes affiche une liste des alertes configurées. La grille récapitulative contient des informations sur l'alerte. Si vous cliquez sur une ligne du résumé des alertes, les détails relatifs à l'alerte en question apparaissent dans la zone Détails de l'alerte du cadre Contenu. Vous pouvez utiliser ces informations pour déterminer si l'alerte répond à vos besoins et si vous voulez vous y abonner.  Si vous êtes propriétaire d'une alerte, vous pouvez la modifier et l'enregistrer. Le tableau suivant répertorie des informations d'ordre général sur l'alerte.  
  
|Colonne Résumé|Sommaire|  
|--------------------|--------------|  
|Nom|Le nom de l'alerte.|  
|Type|Agréger ou Individuel.|  
|Activé|Indique si l'alerte est active et si elle peut être déclenchée.|  
|Priorité|Indique le niveau de gravité du problème signalé par l'alerte.|  
|Sécurité|Une alerte peut être publique ou privée. Tous les utilisateurs peuvent être abonnés à des alertes publiques, tandis que pour s'abonner à des alertes privées, il faut être propriétaire de celles-ci.|  
|Date de création|L'utilisateur ayant créé l'alerte.|  
|Date de création|Date et heure de création de l'alerte.|  
|Date de dernière modification|Date et heure du dernier enregistrement de l'alerte.|  
|Est propriétaire|Indique si vous êtes propriétaire de l'alerte concernée.|  
  
### <a name="alert-details"></a>Détails de l’alerte  
 Le **détails de l’alerte** zone du cadre contenu gestion des alertes fournit des détails sur l’alerte. Vous pouvez utiliser ces informations pour déterminer si l'alerte répond à vos besoins. Vous pouvez également modifier l'alerte dans cette zone. Le tableau suivant décrit les informations détaillées concernant une alerte.  
  
|Nom du champ|Sommaire|  
|----------------|--------------|  
|Nom|Le nom de l'alerte. Le nom de l'alerte est utilisé comme objet du message pour les alertes remises par messagerie et comme nom de fichier pour celles qui sont remises sous la forme d'un fichier. **Remarque :** noms sont limités à 100 caractères et ne peut pas contenir les caractères suivants : ~ ! @# $% ^&amp;* () ;|  
|Message|Texte du message remis avec l'alerte.|  
|Priorité|Indique le niveau de gravité du problème signalé par l'alerte. Les niveaux de priorité possibles sont : Élevé, Moyen et Bas. Ce paramètre permet de déterminer, pour les alertes remises par courrier électronique, le type de l'indicateur d'importance du message.|  
|Propriétaires|Propriétaire de l'alerte. Par défaut, le propriétaire est identique au créateur de l'alerte. Pour entrer plusieurs propriétaires, séparez-les par un point-virgule.|  
|Zone Limite|Cette zone des détails d'alerte s'affiche uniquement pour les alertes d'agrégation.|  
|Compter<br />(Alerte d’agrégation uniquement)|Liste déroulante d'opérations de comparaison.|  
|Valeur<br />(Alerte d’agrégation uniquement)|Valeur limite à laquelle la comparaison s'applique. L'alerte est envoyée uniquement lorsque la valeur correspond aux critères de comparaison. L'alerte ne sera pas renvoyée si l'analyse a été réinitialisée du fait que la condition n'était plus vraie. Par exemple, si l'alerte est définie de sorte qu'un montant de commande supérieur à 1 000 dollars soit signalé, l'alerte n'est pas renvoyée tant que le montant de la commande reste au-dessus de 1 000 dollars. En revanche, lorsque ce montant redescend en dessous des 1 000 €, puis dépasse à nouveau cette limite, l'alerte est renvoyée.|  
|Bouton Requête avancée|Ouvrez la boîte de dialogue Éditeur de requêtes avancé. Cet Éditeur utilise des expressions multidimensionnelles pour définir la requête. Il s'agit d'une fonctionnalité avancée ne devant être utilisée que par des utilisateurs expérimentés. Pour plus d’informations sur le langage de requête d’expressions multidimensionnelles, voir le chapitre 25, « Expressions multidimensionnelles » dans la référence du programmeur OLE DB sur MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkId=58869](http://go.microsoft.com/fwlink/?LinkId=58869).|  
|Zone Restreindre la recherche au dernier|Cette zone des détails d'alerte s'affiche uniquement pour les alertes d'agrégation. Si la case à cocher est sélectionnée, l’alerte est transmise uniquement si la valeur de seuil est atteint pendant la période spécifiée. Si elle n'est pas activée, l'alerte est transmise lorsque la valeur limite est atteinte, quelle que soit la période spécifiée. Par défaut, si des dimensions de temps ont été définies, cette case à cocher est activée. Dans le cas où aucune dimension de temps n'a été définie, cette option n'est pas disponible.|  
|En fonction de la Dimension<br />(Alerte d’agrégation uniquement)|Indique une dimension de temps dans laquelle l'analyse BAM contrôle si la valeur limite a été atteinte.|  
|Duration<br />(Alerte d’agrégation uniquement)|Champ en deux parties constitué d'un champ de texte contenant une valeur numérique et d'une liste déroulante précisant l'unité de mesure. La valeur de la durée doit être supérieure à zéro et inférieure ou égale à la durée définie pour l'agrégation au moment de sa création.|  
|Zone Sécurité d'alerte|Zone de paramétrage de la sécurité.|  
|Autoriser des tiers à voir cette alerte et à s'y abonner|Case à cocher qui, lorsqu'elle est activée, permet aux utilisateurs disposant des autorisations d'accès à la vue sous-jacente d'afficher l'alerte et de s'y abonner. Les utilisateurs peuvent se désabonner à tout moment. Les propriétaires d'alerte et ceux des bases de données peuvent également supprimer un abonné à tout moment.|  
  
### <a name="subscriptions"></a>Abonnements  
 Le **abonnements** zone du cadre contenu gestion des alertes vous permet de s’abonner à une alerte. Le tableau suivant répertorie les informations à fournir pour s'abonner à une alerte.  
  
|Nom du champ|Sommaire|  
|----------------|--------------|  
|Nom d'utilisateur|Alias de l'utilisateur s'abonnant à l'alerte. Cette valeur est automatiquement définie sur l'utilisateur actuel.|  
|Transport|Indique la façon dont l'alerte est transmise. Elle peut être transmise par messagerie ou sous forme de fichier.|  
|Adresse|Indique la destination de l'alerte. Il peut s'agir d'une adresse de messagerie (alertes transmises par courrier électronique) ou d'un emplacement de fichier défini par le système (alertes transmises par fichier). Lorsque plusieurs utilisateurs sont abonnés à une alerte transmise par messagerie, un seul message électronique est envoyé à tous les abonnés. Un abonné peut donc répondre à tous les autres pour leur signaler que le problème a effectivement été résolu.|  
|Bouton Ajouter l'abonné|Permet d'ouvrir la boîte de dialogue correspondante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment définir une alerte](../core/how-to-set-an-alert.md)