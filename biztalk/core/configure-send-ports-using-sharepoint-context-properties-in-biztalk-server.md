---
title: "Comment configurer les Ports d’envoi à l’aide de Windows Sharepoint Services des propriétés de contexte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, InfoPath forms
- configuring [Windows SharePoint Services adapters], InfoPath forms
- Windows SharePoint Services adapters, Windows SharePoint Services
- InfoPath forms, Windows SharePoint Services adapters
- configuring [Windows SharePoint Services adapters], Windows SharePoint Services
- Windows SharePoint Services adapters, send ports
- configuring [Windows SharePoint Services adapters], send ports
- send ports, Windows SharePoint Services adapters
- Windows SharePoint Services, Windows SharePoint Services adapters
ms.assetid: 1ff50fb8-7ba0-47b8-9476-d57413989346
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e766272f33bf23166ba412a76498e4240ab3343b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-send-ports-using-windows-sharepoint-services-context-properties"></a>Configuration des ports d'envoi à l'aide des propriétés de contexte Windows Sharepoint Services
Cette rubrique décrit la configuration des ports d'envoi Windows SharePoint Services, au moment de l'exécution, à l'aide des propriétés de contexte Windows SharePoint Services, à partir d'une orchestration BizTalk. Le même mécanisme peut être utilisé pour configurer les ports d'envoi dynamiques et à liaison tardive Windows SharePoint Services. Les propriétés de configuration pour un port d'envoi dynamique sont définies dans une orchestration au moment de l'exécution. Propriétés de l’adaptateur qui sont exposées dans le **propriétés du Transport Windows SharePoint Services** boîte de dialogue peut également être appliquée à un port d’envoi dynamique ou à liaison tardive. Pour définir les propriétés de configuration d'un port d'envoi dynamique ou à liaison tardive à l'aide des propriétés de contexte de l'adaptateur Windows Sharepoint Services, procédez comme suit :  
  
### <a name="to-set-configuration-properties-for-a-send-port-using-windows-sharepoint-services-adapter-context-properties"></a>Pour définir les propriétés de configuration d'un port d'envoi à l'aide des propriétés de contexte de l'adaptateur Windows Sharepoint Services  
  
1.  Pour les ports d’envoi dynamiques, pour créer un dynamique unidirectionnel port d’envoi, suivez les étapes décrites dans la rubrique [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).  
  
2.  Utilisez un **assignation du Message** mettre en forme dans un **construire un Message** forme dans une orchestration pour définir les propriétés de configuration pour le message sortant. Pour obtenir un exemple montrant comment définir les propriétés de configuration pour un message sortant, consultez [procédure pas à pas : Module 3 - l’accès à des propriétés SharePoint à partir d’une Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md). Le **construire un nouveau message** section de cette rubrique illustre comment définir les propriétés de configuration d’un message sortant. Les propriétés de contexte de l’adaptateur mises en corrélation avec les propriétés qui peuvent être définies dans le **propriétés du Transport Windows SharePoint Services** boîte de dialogue sont répertoriés dans le tableau ci-dessous :  
  
    |Propriété de transport|Propriétés de contexte de l'adaptateur|Type de données|Commentaires|  
    |------------------------|------------------------------|---------------|--------------|  
    |Port de service Web d'adaptateur|WSS.ConfigAdapterWSPort|int|Les valeurs valides sont compris entre 1 et 65 535.<br /><br /> La valeur par défaut est 80.|  
    |Délai d'expiration|WSS.ConfigTimeout|int|Les valeurs valides sont de 1000 à 2147483647<br /><br /> La valeur par défaut est 100 000<br /><br /> Spécifiez une valeur de 0 pour indiquer un délai d'expiration infini.|  
    |URL Dossier de destination|N/A|N/A|Pour les ports dynamiques, elle est définie indirectement en définissant le **Microsoft.XLANGs.BaseTypes.Address** propriété du port dynamique avec une forme expression dans une orchestration. Pour les ports à liaison tardive, cette propriété ne peut pas être définie au moment de l'exécution car elle est toujours remplacée par la valeur du port d'envoi physique.|  
    |Nom du fichier|WSS.Filename|Chaîne|Prend en charge l’utilisation de toutes les macros de nom de fichier qui peut être utilisé dans les propriétés de transport à l’exception de la **%filename%** et **%extension%** macros.|  
    |Alias d'espaces de noms|WSS.ConfigNamespaceAliases|Chaîne|Si un alias d'espace de noms défini pour un message au moment de l'exécution correspond exactement à l'alias d'espace de noms défini pour le port d'envoi vers lequel le message est routé, alors les espaces de noms sont fusionnés et une erreur de routage se produit. Pour empêcher ce problème, assurez-vous que les alias d'espaces de noms spécifiés ne sont pas identiques. Par exemple, si l'expression suivante est utilisée dans une orchestration pour définir l'alias d'espace de noms pour un message :<br /><br /> `Message_Task(WSS.ConfigNamespaceAliases)= "orchns='http://OrderProcess.PurchaseOrder'";`<br /><br /> et si ce message est routé vers un port d’envoi qui spécifie la valeur suivante pour le **Namespace alias** propriété :<br /><br /> orchns='http://OrderProcess.PurchaseOrder '<br /><br /> alors une erreur se produit lorsque BizTalk Server tente de router le message vers ce port d'envoi. Pour résoudre ce problème, vous pouvez spécifier la valeur suivante pour le **Namespace alias** propriété du port d’envoi :<br /><br /> **orchns2**= 'http://OrderProcess.PurchaseOrder'|  
    |Remplacer|WSS.ConfigOverwrite|Chaîne|Les valeurs valides sont :<br /><br /> -« Oui »<br /><br /> -« non »<br /><br /> -« rename »|  
    |URL de site SharePoint|WSS.InListUrl|Chaîne|Pour les ports dynamiques, elle est définie indirectement en définissant le **Microsoft.XLANGs.BaseTypes.Address** propriété du port dynamique avec une forme expression dans une orchestration. Pour les ports à liaison tardive, cette propriété ne peut pas être définie au moment de l'exécution car elle est toujours remplacée par la valeur du port d'envoi physique.|  
    |Intégration de Microsoft Office|WSS.ConfigOfficeIntegration|Chaîne|Les valeurs valides sont :<br /><br /> -« Oui »<br /><br /> -« non »<br /><br /> -« yesformlibrary »<br /><br /> -« facultatif »|  
    |Bibliothèque de documents Modèles|WSS.ConfigTemplatesDocLib|Chaîne|Aucune|  
    |Bibliothèque de documents Modèles de secours|WSS.ConfigCustomTemplatesDocLib|Chaîne|Aucune|  
    |Colonne espaces de noms Modèles de secours|WSS.ConfigCustomTemplatesNamespaceCol|Chaîne|Aucune|  
    |Colonne d'espace de noms des modèles|WSS.ConfigTemplatesNamespaceCol|Chaîne|Aucune|  
    |Colonne `n`|WSS.ConfigPropertiesXml<br /><br /> Nom de la colonne est défini dans \<PropertyName*x*\>*columnname*\</ PropertyName*x* \> champ.|Chaîne|Aucune|  
    |Valeur de la colonne `n`|WSS.ConfigPropertiesXml<br /><br /> Valeur de colonne est définie dans \<PropertySource*x*\>*columnvalue*\</ PropertySource*x* \> champ.|Chaîne|Prend en charge l’utilisation de toutes les macros de nom de fichier qui peut être utilisé dans les propriétés de transport à l’exception de la **%filename%** et **%extension%** macros.|  
  
    > [!NOTE]
    >  Les valeurs fournies pour les propriétés de contexte respectent la casse. Lors de la définition de valeurs de configuration pour un port dynamique avec des propriétés de contexte, veillez à utiliser la casse appropriée, sans quoi une erreur se produit quand BizTalk tente de router le document vers le port d'envoi désigné.  
  
3.  Utilisez une forme expression dans une orchestration pour définir le **Microsoft.XLANGs.BaseTypes.Address** propriété dynamique un port d’envoi. Cette propriété sert à spécifier l'URI vers lequel le port d'envoi dynamique route le message. Pour obtenir un exemple montrant comment définir le **Microsoft.XLANGs.BaseTypes.Address** propriété pour un port d’envoi dynamique voir le **créer une expression** section de la rubrique [procédure pas à pas : Module 3 - Accès aux propriétés SharePoint à partir d’une Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md). Pour plus d’informations sur les propriétés de contexte de l’adaptateur Windows Sharepoint Services, consultez [référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md).  
  
     Il est également possible de définir de manière dynamique certaines propriétés d'un port d'envoi à liaison tardive Windows Sharepoint Services dans une orchestration. Si cela est fait, le port Windows Sharepoint Services est configuré deux fois : la première via les propriétés de contexte Windows SharePoint Services et la seconde via la boîte de dialogue Propriétés du transport Windows SharePoint Services. Par défaut, la configuration spécifiée dans la boîte de dialogue Propriétés du transport Windows SharePoint Services a priorité sur les propriétés de configuration spécifiées dans les propriétés de contexte. Pour utiliser la configuration spécifiée dans les propriétés de contexte, procédez comme suit :  
  
    1.  Pour créer un mappage statique unidirectionnel port d’envoi, suivez les étapes décrites dans la rubrique [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).  
  
    2.  Lorsque vous définissez les propriétés du port d’envoi, définissez l’URI pour le port d’envoi en entrant les valeurs appropriées pour le **URL du Site Sharepoint** et **URL dossier de Destination** propriétés.  
  
    3.  Définir la valeur de la **remplacer** propriété **Orchestration** si vous souhaitez utiliser la valeur définie par la propriété de contexte **WSS. ConfigOverwrite** dans une orchestration.  
  
    4.  Définir le **intégration de Microsoft Office** propriété **Orchestration** si vous souhaitez utiliser la valeur définie par la propriété de contexte **WSS. ConfigOfficeIntegration** dans une orchestration.  
  
    5.  Entrez la valeur **-1** pour les propriétés de port qui utilisent le type de données entier si vous voulez définir ces valeurs avec une propriété de contexte dans une orchestration d’envoi.  
  
    6.  N'entrez aucune valeur pour toute propriété du port d'envoi qui utilise le type de données Chaîne si vous voulez définir ces valeurs avec une propriété de contexte dans une orchestration. Cela ne s’applique pas à la **URL du Site Sharepoint** et **URL dossier de Destination** propriétés. Ces propriétés doivent être spécifiées dans le **propriétés du Transport Windows Sharepoint Services** boîte de dialogue.  
  
    7.  Utilisez un **assignation du Message** mettre en forme dans un **construire un Message** forme dans une orchestration pour définir les propriétés de configuration pour le message sortant. Pour obtenir un exemple montrant comment définir les propriétés de configuration pour un message sortant, consultez [procédure pas à pas : Module 3 - l’accès à des propriétés SharePoint à partir d’une Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md). Le **construire un nouveau message** section de cette rubrique illustre comment définir les propriétés de configuration d’un message sortant.  
  
    8.  Toute propriété du port d'envoi qui est configurée sur la valeur -1 (pour les propriétés utilisant le type de données Entier), sur « Orchestration » (pour les propriétés d'énumération d'une liste déroulante) ou laissée vide (pour les propriétés utilisant le type de données Chaîne), est définie au moment de l'exécution avec la propriété de contexte spécifiée dans l'orchestration.  
  
 Si vous utilisez l'adaptateur Windows SharePoint Services pour recevoir des formulaires InfoPath avec des pièces jointes incorporées, puis envoyer les formulaires InfoPath à une bibliothèque de documents SharePoint, effectuez les opérations suivantes pour conserver les instructions de traitement InfoPath présentes dans le formulaire :  
  
### <a name="to-preserve-infopath-processing-instructions-for-infopath-forms-with-embedded-attachments-processed-by-biztalk-server"></a>Pour conserver les instructions de traitement InfoPath pour les formulaires InfoPath, avec des pièces jointes incorporées, traités par BizTalk Server  
  
1.  Si vous utilisez un mappage dans l’orchestration pour mapper les données d’un formulaire InfoPath à un autre formulaire InfoPath, assurez-vous que vous avez défini le **copier les Instructions (traitement)** propriété dans la carte pour **Oui**. Ce paramètre est défini sous la **en-tête personnalisé** section de la **propriétés de la grille** page pour la carte.  
  
2.  Si vous n'utilisez pas de mappage dans l'orchestration, mettez à jour le message de sortie à l'aide de l'expression suivante dans une forme Assignation de message :  
  
    ```  
    NewMessage(XMLNORM.ProcessingInstructionOption) = 1;  
    NewMessage(XMLNORM.ProcessingInstruction) = "<?mso-infoPath-file-attachment-present?>"  
    ```  
  
     Dans l’expression ci-dessus, *NewMessage* est le message de sortie que vous ajoutez aux instructions de traitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)