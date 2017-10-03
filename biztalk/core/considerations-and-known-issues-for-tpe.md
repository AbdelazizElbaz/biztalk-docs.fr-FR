---
title: "Considérations et problèmes connus pour l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, known issues
- planning, Tracking Profile Editor
- Tracking Profile Editor, planning
ms.assetid: e96d85e0-e9ae-434a-b54e-5950f4a2b9c6
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d630b2cfa5cca1d7a441796ef8c555d02bb04910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-and-known-issues-for-tpe"></a>Considérations diverses et problèmes connus relatifs à l'Éditeur de modèle de suivi
Tenez compte des points suivants quand vous utilisez des modèles de suivi et l'Éditeur de modèle de suivi.  
  
## <a name="naming-folders-in-the-tpe"></a>Dénomination des dossiers dans l'Éditeur de modèle de suivi  
 Considérez les conventions d'affectation de noms suivantes lorsque vous donnez un nom aux dossiers dans l'Éditeur de modèle de suivi :  
  
-   La longueur totale du nom des dossiers et des valeurs d'instance d'élément de données ne doit pas excéder 128 caractères.  
  
-   Pour les dossiers Continuation et ContinuationID, la dénomination des dossiers représente la mise en corrélation de deux orchestrations. Par exemple, si l'orchestration A est le parent de l'orchestration B, l'orchestration A contient un dossier de continuation dont le nom est directement mappé sur le dossier ContinuationID dans l'orchestration B.  
  
## <a name="developing-orchestrations-for-the-tpe"></a>Développement d'orchestrations pour l'Éditeur de modèle de suivi  
 Il est impossible de mapper une orchestration sur une activité d'entreprise si elle commence ou s'achève par une forme non valide. Le moteur d'orchestration n'autorise pas le suivi pour certaines formes. Celles-ci sont les suivantes :  
  
-   Assignation de messages  
  
-   Transformation  
  
-   Groupe (Tâche)  
  
-   Suspendre  
  
-   Boucle (Tant que)  
  
-   Agence  
  
-   Terminate  
  
-   Levée d'exception  
  
-   Intercepter  
  
-   Tant que  
  
 Suivez les instructions suivantes quand vous effectuez un mappage sur des activités d'entreprise afin que l'Éditeur de modèle de suivi et d'autres outils BAM puissent les utiliser :  
  
-   Pour la forme Groupe, utilisez une forme Étendue non transactionnelle.  
  
-   Intégrez la forme Tant que dans une forme Étendue non transactionnelle.  
  
-   Pour la forme Terminer, il n'y pas de parade car l'événement de fin de cette forme n'intervient jamais dans un scénario normal.  
  
-   Ne commencez pas et ne terminez pas des planifications par les formes pour lesquelles les opérations glisser-déposer ne sont pas autorisées.  
  
## <a name="applying-tracking-profiles-that-monitor-running-processes"></a>Application de modèles de suivi analysant les processus en cours  
 La mise à jour d'un modèle de suivi peut avoir des conséquences sur les instances d'activité en cours si l'activité comprend une continuation d'analyse BAM. Notamment, si la mise à jour du modèle de suivi indique une interception en aval des données pour un élément d'activité déjà enregistré, il est possible que la valeur d'origine soit remplacée. Par définition, un flux d'événements unique ne sera pas affecté par les mises à jour du modèle de suivi, car chaque objet de flux est lié à la version du modèle en place au moment où l'activité ou le flux a démarré. Cependant, les continuations étant le moyen de mettre en corrélation plusieurs flux d'événements, les flux n'ayant pas encore été lancés au moment de la mise à jour du modèle récupèrent les modifications dans la mise à jour. Il existe alors un risque pour les données d'être remplacées, comme décrit plus haut. Pour plus d’informations sur les continuations, consultez [Continuation d’activités](../core/activity-continuation.md) et [comment créer une Continuation](../core/how-to-create-a-continuation.md).  
  
## <a name="tracking-profiles-without-a-send-or-receive-shape-from-which-to-draw-message-properties"></a>Modèles de suivi dépourvus d'une forme Envoi ou Réception dans laquelle puiser les propriétés de message  
 Les continuations effectuent le suivi des activités par le biais de propriétés de contexte ou de données de charge communes à toutes les activités. Les propriétés telles que Message ID, Service ID et Instance ID changent de valeur d'une activité à l'autre.  
  
 Pour gérer ce contexte, vous pouvez créer des modèles de suivi en ayant recours aux méthodes suivantes :  
  
-   Si une orchestration envoie un message à une autre orchestration via une liaison dynamique, une valeur de données de charge unique globale peut être utilisée pour la continuation.  
  
-   Si le message ne renferme pas de données de charge uniques, l'ID d'échange du message peut être utilisé. Pour vous servir de cet ID, vous devez effectuer son suivi dans la même forme Réception. L'ID d'échange variant à chaque nouveau message créé, vous ne pouvez pas l'utiliser si vous créez un nouveau message. Il n'est pas fiable d'effectuer le suivi de l'ID d'échange à partir d'une autre forme que les formes Réception et Envoi.  
  
-   Vous pouvez également utiliser l'ID de message tant qu'est utilisé dans l'orchestration exactement le même message que celui reçu du pipeline, autrement dit, le port d'orchestration est lié à un pipeline, et une forme Réception et l'ID de message font l'objet d'un suivi à partir de cet emplacement. Si vous procédez au suivi de l'ID de message à partir d'une autre forme, son utilisation dans les continuations sera impossible.  
  
-   Si une orchestration appelle une autre orchestration et aucun message n’est transmis, ou une orchestration appelle une autre orchestration mais que l’appelé ne pas avoir n’importe quel construire, réception ou forme envoi où les valeurs de données de charge utile peuvent être récupérées, l’utilisateur peut utiliser l’ID d’instance. L’ID d’instance des orchestrations appelées ne change pas.  
  
-   Si l'orchestration charge une autre orchestration via un appel d'exécution plutôt que de l'appeler directement, il n'y a alors aucun moyen d'utiliser des propriétés de message statique pour effectuer le suivi de l'activité. L'utilisateur ne peut pas activer une continuation. La seule manière qu'un suivi puisse être réalisé est qu'un message soit transmis via le pipeline qui contient les données de charge uniques sur lesquelles le suivi doit être effectué.  
  
## <a name="you-cannot-use-a-session-id-as-a-continuation-token-for-pass-through-pipelines"></a>Vous n'êtes pas autorisé à utiliser un ID de session en tant que jeton de continuation pour les pipelines de transfert  
 Dans un modèle de suivi, lorsque vous sélectionnez des éléments dans une charge de message, le modèle de suivi est lié au schéma de ce message. La valeur du nom du schéma est une valeur null dans les pipelines de transfert. Lorsque l'analyse BAM tente de charger la configuration par nom de port et par nom de schéma, elle ne peut établir de correspondance avec le schéma d'ID de session et aucune donnée ne fait l'objet d'un suivi par le moteur.  
  
 Pour les pipelines de transfert, vous pouvez soit supprimer l'ensemble du suivi de charge du modèle de suivi, soit utiliser des pipelines XML si vous n'avez pas besoin d'effectuer le suivi des données de charge.  
  
## <a name="using-unique-port-names"></a>Utilisation de noms de port uniques  
 Lorsque vous énumérez des ports bidirectionnels, l'Éditeur de modèle de suivi les affiche sous la forme de deux ports logiques : un port d'envoi et un port de réception. Chacun de ces ports logiques apparaît avec le même nom. BizTalk Server vous permet de créer des ports unidirectionnels et bidirectionnels portant les mêmes noms. Ainsi, vous pouvez créer un port bidirectionnel et l'appeler « Port1 » puis créer un port de réception et l'intituler de la même manière. Dans ce cas, l'Éditeur de modèle de suivi affiche le port de réception une fois et le port bidirectionnel deux fois : une fois comme port de réception, l'autre comme port d'envoi.  
  
 L'Éditeur appliquera alors les modèles de suivi aux deux ports de réception. Afin d'éviter toute confusion, nous vous recommandons d'attribuer des noms uniques aux ports.  
  
## <a name="using-tpe-orchestrations-with-a-parallel-shape-as-the-first-shape"></a>Utilisation d'orchestrations de l'Éditeur de modèle de suivi avec une forme Parallèle en tant que forme initiale  
 Si vous faites commencer une orchestration par une forme Branche, Parallèle ou Écouter, vous ne pouvez pas mapper un ID d'activité sur l'une de ces branches. Dans le cas d'un traitement parallèle, vous pouvez mapper l'ActivityID au-dessus de la forme Branche. Vous pouvez également laisser l'analyse BAM générer l'ID d'activité pour éviter le problème que constitue la position d'une forme Parallèle en haut de l'orchestration.  
  
> [!IMPORTANT]
>  Mapper une activité sur plusieurs chemins et mapper l'ActivityID sur un chemin unique de la forme Branche génère une erreur lorsque le traitement suit le chemin sur lequel l'ActivityID n'est pas mappé.  
  
## <a name="availability-of-message-properties-at-design-time"></a>Disponibilité des propriétés de message au moment de la conception  
 Lorsque vous créez des modèles de suivi, les propriétés de message ne sont pas toutes disponibles. Ce cas de figure se rencontre souvent lorsque la forme d'où les propriétés de message sont mappées se trouve en haut d'une orchestration. La valeur des propriétés de message est alors null.  
  
 Ce cas se présente par exemple quand une forme Écouter est la première forme d'une orchestration. Lorsque les propriétés de message sont mappées à partir de cette forme, seules les propriétés suivantes ont des valeurs : InstanceID, ServiceID et ServiceClassID. (à ce stade, MessageID ne fait pas partie de l'étendue et a une valeur null).  
  
## <a name="you-cannot-map-shapes-inside-a-loop-shape-to-report-a-milestone"></a>Vous n'êtes pas autorisé à mapper des formes au sein d'une forme Boucle pour signaler une étape majeure  
 L'Éditeur de modèle de suivi restreint les sources de mappage contenues dans une forme Boucle aux activités mappées à des éléments situés à l'extérieur de la boucle.  
  
 Les activités de bouclage sont des actions mises en boucle (qui se répètent) dans une orchestration. Il est possible de capturer les événements d'actions mises en boucle dans une orchestration. Pour ce faire, vous devez créer une autre activité et mapper l'ensemble des données et des étapes majeures de cette nouvelle activité dans la boucle. Cette opération est nécessaire étant donné que le traitement des données dans la boucle se répètera plusieurs fois par exécution planifiée.  
  
 Par exemple, si vous avez un bon de commande avec plusieurs éléments de ligne traités dans une boucle, les questions du type « les bons de commande doivent prix unitaires de 100 $? » sont ambiguës. Voici ce que seraient des questions sans équivoque :  
  
 Quels sont les bons de commande contenant des éléments de ligne avec un prix de 100$ ?  
  
 Quels sont les bons de commande contenant des prix unitaires total/min/max de 100 $ ?  
  
 Pour poser des questions sans ambiguïté, il faut bien distinguer éléments de ligne et bon de commande. Dans l'Éditeur de modèle de suivi, l'activité racine (un bon de commande par exemple) est mappée sur toutes les actions extérieures à la boucle. L'activité enfant (un élément de ligne par exemple) est mappée sur les actions situées dans la boucle.  
  
 La méthode la plus classique pour utiliser ces types de constructions est de décomposer la boucle récurrente et d'avoir une activité associée basée sur l'activité interne associée à l'activité externe.  
  
 Vous devez utiliser un élément de charge comme ActivityID pour l'activité racine et rendre cet élément de charge disponible dans certains messages dans la boucle. Mappez l'activité sur le nœud de relation affiché sous l'activité enfant et nommez-la en tant qu'activité racine.  
  
## <a name="tracking-profiles-spanning-multiple-applications"></a>Modèles de suivi englobant plusieurs applications  
 Si un modèle de suivi englobe plusieurs applications, il doit être déployé après toutes les applications de la solution. Si le modèle de suivi n’est pas le dernier élément déployé, vous recevez le message suivant, «**source de mappage introuvable.**», lors de l’Assistant Déploiement appellera BTTDeploy.exe.  
  
## <a name="mapping-multiple-biztalk-server-artifacts-to-a-document-reference-url-or-messageid-nodes"></a>Mappage de plusieurs artefacts de BizTalk Server sur des nœuds Document Reference URL ou MessageID  
 L'Éditeur de modèle de suivi vous permet de faire glisser plusieurs artefacts de BizTalk Server et de les déposer dans le même nœud Document Reference URL ou MessageID.  
  
 Dans le cas où plusieurs sources sont mappées sur le même élément d'une activité BAM, le dernier artefact rencontré durant le traitement de l'analyse BAM est celui qui est conservé dans les données de suivi et peut être affiché dans le portail BAM.  
  
## <a name="updating-btt-versions-to-match-biztalk-solution-versions"></a>Mise à jour de versions de BTT correspondant aux versions de solution BizTalk  
 En tant que développeur ou administrateur BAM, vous pouvez maintenir la synchronisation des versions entre les modèles de suivi et les solutions BizTalk en automatisant la mise à jour avec le fichier BTT. Pour ce faire, modifiez le **Version** d’attribut dans le **DataLevel** élément du fichier BTT. Dans l'exemple d'élément ci-dessous, vous devez modifiez les informations de version dans les attributs TargetAssemblyName et SchemaName.  
  
```  
<DataLevel Name="City" SourceTypeSelected="Messaging Payload" TargetAssemblyName="TheImplementationOfOrderMgmt, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c5b33e44ffa4658b" SchemaName="TheImplementationOfOrderMgmt.PurchaseOrder,TheImplementationOfOrderMgmt, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c5b33e44ffa4658b" SomXPath="/*[local-name()='<Schema>' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='PurchaseOrder' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='Header' and namespace-uri()='']/*[local-name()='ShipTo' and namespace-uri()='']/@*[local-name()='City' and namespace-uri()='']" XPath="/*[local-name()='PurchaseOrder' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='Header' and namespace-uri()='']/*[local-name()='ShipTo' and namespace-uri()='']/@*[local-name()='City' and namespace-uri()='']" IsBeginActivity="true" IsEndActivity="false">  
```  
  
## <a name="some-orchestration-shapes-cannot-be-tracked-in-the-tpe"></a>Certaines formes d'orchestration ne peuvent pas faire l'objet d'un suivi dans l'Éditeur de modèle de suivi  
 Le moteur d'orchestration ne génère pas d'événements pour les formes ci-dessous. Ces formes ne peuvent donc pas faire l'objet d'un suivi ou d'un mappage dans l'Éditeur de modèle de suivi :  
  
-   Tâche  
  
-   Toutes les branches  
  
-   Suspendre  
  
-   Terminate  
  
-   Levée d'exception  
  
-   Intercepter  
  
-   AssignationMessage (car elle fait partie de la forme Construire)  
  
-   Transformer (car elle fait partie de la forme Construire)  
  
-   Boucle  
  
## <a name="tpe-not-retrieving-deployed-tracking-profiles"></a>L'Éditeur de modèle de suivi ne récupère pas les modèles de suivi déployés  
 Après une mise à niveau ou un redéploiement, vous pouvez avoir du mal à récupérer les modèles de suivi déployés. Ces difficultés peuvent être dues à une erreur liée au nom du serveur sur lequel la base de données BizTalkMgmtDb est stockée dans le registre.  
  
 La base de données BizTalkMgmtDb est inscrite dans le registre pendant la configuration de groupe. L'Éditeur de modèle de suivi utilise cette entrée pour rechercher la base de données d'importation principale et filtrer les modèles de suivi.  
  
 Pendant la configuration, il est possible d'entrer le nom du serveur sous plusieurs formats. Exemple :  
  
-   mgmtsvr1316267,15001\inst  
  
-   MGMTSVR1316267\inst,15001  
  
 L'Éditeur de modèle de suivi effectue une comparaison de chaînes de base lorsqu'il utilise l'entrée du registre. Pour récupérer les profils de suivi déployé, il est nécessaire d’inspecter les noms de serveur et de base de données stockées et entrez-les dans l’éditeur **définir la base de données de gestion** boîte de dialogue.  
  
#### <a name="to-determine-the-syntax-for-server-and-database-names-and-enter-it-in-the-biztalk-management-database"></a>Pour déterminer la syntaxe du nom du serveur et de la base de données, puis les entrer dans la base de données de gestion BizTalk.  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **Gestionnaire de Configuration personnalisée**. Pour plus d’informations sur l’utilisation de la **Gestionnaire de Configuration personnalisée**, consultez [configurer BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).  
  
2.  Dans le volet de navigation, sélectionnez **groupe** pour ouvrir la page de configuration de groupe.  
  
3.  Dans le **banques de données** grille, observez les formats de la **nom du serveur** et le **nom de la base de données**.  
  
4.  Ouvrez l’éditeur, puis sélectionnez le **outils** élément de menu.  
  
5.  Sélectionnez le **définir la base de données de gestion** élément de menu pour ouvrir la **définir la base de données de gestion** boîte de dialogue.  
  
6.  Dans le **SQL Server** texte, entrez le nom du serveur qui a été utilisé dans le **nom du serveur** champ le **banques de données** gridon le **Gestionnaire de Configuration personnalisée**  page de groupe.  
  
7.  Dans le **nom de la base de données** texte, entrez le nom de la base de données qui a été utilisé dans le **nom de la base de données** champ le **banques de données** gridon le **Configuration personnalisée Gestionnaire** page de groupe.  
  
8.  Cliquez sur le **OK** bouton pour enregistrer les entrées.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’éditeur](../core/using-the-tpe.md)   
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)