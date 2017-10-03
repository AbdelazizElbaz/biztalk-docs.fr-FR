---
title: "Configurer le contexte d’application à l’aide des propriétés de contexte de message dans Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b76788-5c81-4bb4-8ef6-b1439955ea97
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43f0128b0d1da7ddfb9a29b697d5d5073f69dd33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-application-context-using-message-context-properties-in-oracle-e-business-suite"></a>Configurer le contexte d’application à l’aide des propriétés de contexte de message dans Oracle E-Business Suite
Pour effectuer des opérations sur les artefacts d’Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez définir le contexte d’application de manière appropriée. Vous pouvez définir le contexte d’application comme suit :  
  
-   En spécifiant les propriétés de liaison qui expose de l’adaptateur. Pour plus d’informations, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
-   À l’aide des propriétés de contexte de message qui expose de l’adaptateur. Vous devez prendre en compte les éléments suivants lors de la définition du contexte d’application à l’aide des propriétés de contexte de message.  
  
    -   Vous pouvez définir des valeurs uniquement pour les **ApplicationShortName**, **OrganizationID**, **ResponsibilityKey**, et **ResponsibilityName** à l’aide de propriétés de contexte du message. Le nom d’utilisateur et mot de passe, vous devez utiliser les propriétés de liaison. La valeur spécifiée pour le **ResponsibilityKey** propriété de contexte de message remplace la valeur spécifiée pour le **ResponsibilityName** propriété de contexte de message.  
  
    -   Si vous définissez le contexte d’application à l’aide des propriétés de liaison et les propriétés de contexte de message, les valeurs spécifiées pour les propriétés de contexte de message sont prioritaires et remplacent les valeurs spécifiées pour les propriétés de liaison. Toutefois, par exemple, si vous spécifiez le nom court d’application comme une propriété de contexte de message et le nom d’organisation ID et la responsabilité comme propriétés de liaison, seule la valeur pour le nom court de l’application provient de la propriété de contexte de message. Le reste sont récupérées à partir des propriétés de liaison appropriées.  
  
 Pourquoi utiliser des propriétés de contexte de message sur la liaison des propriétés pour définir le contexte de l’application ? Si vous définissez le contexte d’application à l’aide des propriétés de liaison, WCF-Custom port d’envoi le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] peut être utilisé uniquement pour l’ID d’organisation spécifique, la responsabilité et application que vous avez spécifié pour les propriétés de liaison. En revanche, si vous utilisez la propriété de contexte de message, vous pouvez configurer un port d’envoi WCF-Custom « générique » et définir le contexte d’application au niveau du message.  
  
 Les clients de l’adaptateur doivent définir le message de propriétés de contexte sur le message qui est envoyé pour appeler une opération sur Oracle E-Business Suite pour Oracle E-Business Suite. Les messages dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sont immuables. Par conséquent, les clients doivent d’abord créer un message à partir du message existant et définir ensuite des propriétés de contexte du message sur le nouveau message. Pour la procédure décrite dans cette section, supposez que le message existant est appelé **demande**, et le nouveau message est appelé **New_Request**.  
  
## <a name="set-the-message-context-properties-for-biztalk-applications"></a>Définir des propriétés de contexte pour les applications BizTalk le message  
  
1.  Ouvrez le projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2.  Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter des références**.  
  
3.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **Parcourir** onglet, puis accédez à l’emplacement où le fichier DLL du schéma de propriété BizTalk pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est disponible.  
  
     Cette DLL, `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`, est installé par le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] à \< *lecteur d’installation*> : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin.  
  
4.  Sélectionnez le fichier DLL, puis cliquez sur **ajouter**.  
  
5.  Dans l’orchestration BizTalk, ajoutez un message, **New_Request**. Pour le **Type de Message** propriété, veillez à sélectionner le même type que le message de demande existante.  
  
6.  Avant de la forme envoi à l’aide de laquelle le message est envoyé au port d’envoi, ajoutez une forme construire un Message et dans laquelle une forme assignation du Message.  
  
7.  Double-cliquez sur la forme assignation du Message pour ouvrir **Éditeur d’Expression BizTalk**.  
  
8.  Dans **Éditeur d’Expression BizTalk**, ajoutez le code suivant, puis cliquez sur **OK**:  
  
    ```  
    New_Request = Request;  
    New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ApplicationShortName) = "AR";  
    New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityKey) = "RECEIVABLES_VISION_OPERATIONS";  
    New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityName) = "Receivables, Vision Operations (USA)";  
    New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.OrganizationId) = "204";  
    ```  
  
    > [!IMPORTANT]
    >  La valeur spécifiée pour le **ResponsibilityKey** propriété de contexte de message remplace la valeur spécifiée pour le **ResponsibilityName** propriété de contexte de message.  
  
9. Assurez-vous que le traitement de l’orchestration est effectué à l’aide de la **New_Request** message.  
  
10. Avant de pouvoir déployer cette orchestration dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez ajouter la référence d’assembly pour `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll` dans l’application BizTalk où vous déployez l’orchestration. Pour déployer un assembly dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]:  
  
    1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
    2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**et puis l’application à laquelle vous souhaitez ajouter un assembly BizTalk.  
  
    3.  Avec le bouton droit **ressources**, pointez sur **ajouter**, puis cliquez sur **assemblys BizTalk**.  
  
    4.  Dans le **ajouter des ressources** boîte de dialogue, cliquez sur **ajouter**, accédez au dossier contenant le fichier d’assembly BizTalk, qui est \< *lecteur d’installation*> : \ Programme Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin. Sélectionnez le `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll` de fichiers, puis cliquez sur **ouvrir**.  
  
    5.  Sur le **Options** onglet, spécifiez les options d’installation de l’assembly BizTalk dans le global assembly cache (GAC), puis cliquez sur **OK**.  
  
## <a name="set-the-language-for-performing-operations"></a>Définir la langue pour effectuer des opérations  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la fonctionnalité de prise en charge multilingue (MLS) d’Oracle E-Business Suite, et vous permet de spécifier une langue lors de l’exécution des opérations. L’adaptateur expose le **langage** propriété de contexte pour spécifier une langue pour effectuer des opérations de message.  
  
 La valeur spécifiée pour le **langage** propriété de contexte de message remplace la valeur de la **langage** liaison de la propriété sous la **MlsSettings** propriété de liaison. Pour plus d’informations sur la **MlsSettings** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
