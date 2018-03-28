---
title: AS2 via File (exemple BizTalk Server) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fed2344-8181-4c85-a2ef-a421fc40dce1
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14d4c077cce861e94f6c2cdc0bfc6f4a14669340
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="as2-over-file-biztalk-server-sample"></a>AS2 via FILE (exemple BizTalk Server)
L'exemple AS2 via FILE présente la réception d'un message AS2 via un emplacement de réception FILE. Cela vous permet d'utiliser un adaptateur FILE pour recevoir le message AS2, plutôt qu'un adaptateur HTTP normalement utilisé. Pour ce faire, cette solution écrit les en-têtes HTTP du message AS2 dans la propriété de contexte InboundHTTPHeaders, comme requis par le Décodeur AS2.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple illustre le traitement des en-têtes HTTP d'un message AS2 sans adaptateur HTTP. Plus précisément, cet exemple effectue les opérations suivantes :  
  
1.  Lorsque vous déposez le message test dans un dossier d'entrée, l'emplacement de réception FILE le récupère.  
  
2.  Le composant de pipeline personnalisé dans le pipeline de réception AS2 personnalisé traite le message, en écrivant ses en-têtes HTTP dans la propriété de contexte InboundHTTPHeaders.  
  
    > [!NOTE]
    >  En cas d'échec du traitement du message en aval du composant de pipeline personnalisé, la reprise du traitement du message risque d'être difficile car il est déjà converti en code XML.  
  
3.  Le Décodeur AS2 dans le pipeline de réception personnalisé traite le message, en lisant les propriétés dans la propriété de contexte InboundHTTPHeaders.  
  
4.  Un port d'envoi s'abonne au message XML généré par le pipeline de réception, le transmet par l'intermédiaire d'un pipeline d'envoi PassThrough et le dépose dans un dossier de sortie.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Cet exemple se trouve dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dossier d’installation : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AS2\AS2 Over File.  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|AS2OverFile.csproj|Projet contenant le code du composant de pipeline personnalisé.|  
|AS2OverFile.sln|Solution contenant le projet AS2OverFile.btproj.|  
|Program.cs|Inclut des classes représentant des données d'en-têtes.|  
|SampleMessage.txt|Exemple de message contenant des en-têtes HTTP.|  
  
## <a name="implementing-and-running-this-sample"></a>Implémentation et exécution de cet exemple  
 Pour implémenter l'exemple AS2 via FILE, vous devez effectuer les opérations suivantes :  
  
-   Créer et déployer le projet BizTalk pour cet exemple, puis créer le composant de pipeline personnalisé  
  
-   Créer un pipeline personnalisé à l'aide du composant de pipeline personnalisé, puis créer et déployer un projet avec ce pipeline personnalisé  
  
-   Créer des dossiers de fichiers d'entrée et de sortie  
  
-   Configurer un port et un emplacement de réception, puis activer l'emplacement de réception  
  
-   Configurer un port d'envoi, puis le démarrer  
  
-   Créer un tiers pour l'envoi de l'exemple de message.  
  
#### <a name="to-build-a-custom-pipeline-with-the-as2-over-file-emulator-pipeline-component"></a>Pour créer un pipeline personnalisé avec le composant de pipeline Émulateur AS2 via FILE  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le projet AS2OverFile dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AS2\AS2 Over File.  
  
2.  Créez un fichier de clé de nom fort, ouvrez la boîte de dialogue Propriétés du projet AS2OverFile, puis attribuez le fichier de clé au projet.  
  
3.  créer le projet ;  
  
4.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez un projet BizTalk nommé AS2OverFile_Pipeline.  
  
5.  Cliquez sur le projet AS2OverFile_Pipeline, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
6.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **fichiers de Pipeline** dans le volet gauche, sélectionnez **Pipeline de réception** dans le volet droit, nommez le pipeline AS2OverFile_ Receive.btp, puis cliquez sur **ajouter**.  
  
7.  Cliquez sur **vue** dans la barre de menus, puis cliquez sur **boîte à outils** pour afficher la boîte à outils.  
  
8.  Dans la boîte à outils, cliquez sur **composants de Pipeline BizTalk**, puis cliquez sur **choisir des éléments de**.  
  
9. Dans le **choisir des éléments de boîte à outils** boîte de dialogue, cliquez sur le **composants de Pipeline BizTalk** onglet. Cliquez sur **émulateur AS2 via File**, puis cliquez sur **OK**.  
  
10. Ajoutez le fichier AS2OverFile.dll au GAC (Global Assembly Cache) en ouvrant une invite de commandes [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], puis en exécutant la commande `gacutil /if "<file name and path>"` sur Microsoft.BizTalk.Sdk.Components.AS2OverFile.dll dans le dossier \AS2 Over File\obj\Debug.  
  
11. Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], faites glisser le composant de pipeline émulateur AS2 via File à partir de la boîte à outils dans le **Decode** étape du pipeline personnalisé.  
  
12. Faites glisser le composant décodeur AS2 dans le **Decode** étape du pipeline personnalisé, une fois le composant AS2 via File.  
  
    > [!NOTE]
    >  Si vous voulez générer un MDN, ajoutez un Désassembleur AS2 dans l'étape Désassembler du pipeline personnalisé. Si vous ne renvoyez pas de MDN, le Désassembleur AS2 n'est pas nécessaire.  
  
13. Créez un fichier de clé de nom fort, ouvrez la boîte de dialogue Propriétés du projet AS2OverFile_Pipeline, puis attribuez le fichier de clé au projet.  
  
14. Construisez et déployez le pipeline personnalisé.  
  
15. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, ajoutez le pipeline personnalisé au nœud Pipelines en cliquant sur le nœud Pipelines, puis en cliquant sur **Actualiser**.  
  
#### <a name="to-implement-the-solution-for-this-sample"></a>Pour implémenter la solution de cet exemple  
  
1.  Dans l'Explorateur Windows, dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AS2\AS2 Over File, créez un dossier d'entrée In et un dossier de sortie Out.  
  
2.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port de réception unidirectionnel nommé AS2OverFile_Receive. Dans le port de réception, créez un emplacement de réception avec les propriétés suivantes :  
  
    |Propriété|Paramètre|  
    |--------------|-------------|  
    |Nom|AS2OverFile_Receive|  
    |Type|FILE|  
    |Dossier de réception|[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AS2\AS2 Over File\In|  
    |Masque de fichier|*.txt|  
    |Pipeline de réception|AS2OverFile|  
  
3.  Dans le nœud emplacements de réception, avec le bouton droit le AS2OverFile_Receive emplacement de réception, puis cliquez sur **activer**.  
  
4.  Dans le nœud Ports d'envoi, créez un port d'envoi unidirectionnel statique avec les propriétés suivantes :  
  
    |Propriété|Paramètre|  
    |--------------|-------------|  
    |Nom|AS2OverFile_Send|  
    |Type|FILE|  
    |Dossier de réception|[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AS2\AS2 Over File\Out|  
    |Masque de fichier|%IDmessage%.xml|  
    |Pipeline d’envoi|PassThrough|  
    |Filtre|BTS.REceivePortName == AS2OverFile_Receive|  
  
5.  Dans le nœud Ports d’envoi, cliquez sur le port d’envoi AS2OverFile_Send, puis cliquez sur **Démarrer**.  
  
6.  Dans le nœud Tiers, créez un tiers nommé « Partenaire ». Dans la liste d’alias, ajoutez un alias avec un **nom** de **EDIINT-AS2 From Value**, un **qualificateur** de **AS2-de**et un  **Valeur** de **partenaire**.  
  
 BizTalk Server est maintenant prêt à utiliser avec cet exemple.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 Utilisez la procédure suivante pour exécuter l'exemple AS2 via FILE.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Copiez le fichier SampleMessage.txt du dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AS2\AS2 Over File dans le dossier \AS2 Over File\In.  
  
2.  Vérifiez qu'un message XML de sortie est déposé dans le dossier de sortie \AS2 Over File\Out.  
  
3.  Ouvrez le message d’entrée SampleMessage.txt dans un éditeur de texte et ouvrez le message de sortie \<GUID\>.xml dans un éditeur de texte. Vérifiez que le message d'entrée SampleMessage.txt a des en-têtes HTTP (et AS2) et que le message de sortie n'a pas d'en-têtes HTTP.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [EDI et AS2 (dossier d’exemples BizTalk Server)](../core/edi-and-as2-biztalk-server-samples-folder.md)   
 [Envoi d’un message AS2 via un port d’envoi FILE](../core/sending-an-as2-message-over-a-file-send-port.md)