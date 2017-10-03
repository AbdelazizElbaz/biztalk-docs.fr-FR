---
title: Windows SharePoint Services 4.0 de prise en charge | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84be7aa0-2ff2-4e40-9c39-5cb89549c636
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f3fedbdc4217ef5379b5e890568346a565a235
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-40-support"></a>Prise en charge de Windows SharePoint Services 4.0
L'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] offre une parité fonction/fonctionnalité avec l'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]. L'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] prend également en charge les fonctionnalités suivantes disponibles avec Windows SharePoint Services 4.0 :  
  
-   Envoi de messages à un site blog Windows SharePoint Services 4.0.  
  
-   Envoi de messages à et réception de messages d'un site Wiki Windows SharePoint Services 4.0.  
  
 L'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ne prend pas en charge les fonctions suivantes disponibles dans Windows SharePoint Services 4.0 :  
  
-   **La Corbeille**: l’adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] carte ne prend pas en charge la réception, ou explicitement, l’envoi de messages de/à la Corbeille.  
  
-   **Répertorie les dossiers**: l’adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] peut envoyer des messages à des listes, mais il ne peut pas recevoir de messages de listes. Windows SharePoint Services 4.0 prend en charge les dossiers dans les listes mais l'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ne prend pas en charge cette fonction. Par conséquent, l'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ne peut pas créer d'éléments de liste dans un dossier de liste autre que le dossier racine.  
  
-   Les sections suivantes décrivent de manière plus détaillée l'utilisation de l'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] pour envoyer des messages à un site blog Windows SharePoint Services 4.0 et l'envoi et la réception de messages à/d'un site Wiki Windows SharePoint Services 4.0.  
  
## <a name="sending-to-a-windows-sharepoint-services-40-blog-site"></a>Envoi à un site blog Windows SharePoint Services 4.0  
 Dans un site blog Windows SharePoint Services 4.0, les messages sont stockés dans le **publie** liste et les catégories sont définies dans le **catégories** liste.  
  
 Pour publier un message sur un site blog Windows SharePoint Services 4.0, entrez les valeurs suivantes dans l’adaptateur **propriétés du Transport** boîte de dialogue lors de la configuration d’un port d’envoi qui utilise l’adaptateur Windows SharePoint Services :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|URL Dossier de destination|URL du dossier de destination de la liste Messages, relative au site SharePoint, par exemple « Listes/Messages ».|  
|URL de site SharePoint|URL du site blog Windows SharePoint Services 4.0, par exemple http://*\<nom_serveur >*/sites/blog/où  *\<nom_serveur >* est un espace réservé pour le nom réel du serveur Web.|  
  
 Puis définissez les valeurs pour le **catégorie**, **publié**, **titre**, et **corps** propriétés pour le blog de validation par le paramètre correspondant valeurs de WSS. Propriété de contexte ConfigPropertiesXml du message. Cela est possible avec un pipeline personnalisé ou dans une orchestration. Par exemple, l’expression suivante dans une orchestration définit des valeurs dans le fichier WSS. Propriété de contexte ConfigPropertiesXml du message Message_Out.  
  
```  
int_Category = 1;  
str_Published = Microsoft.SharePoint.Utilities.SPUtility.CreateISO8601DateTimeFromSystemDateTime(System.DateTime.Now);  
// requires a reference to Microsoft.SharePoint.dll  
str_Title = "This is the title of the post from the WSS adapter";  
str_Body = "This is the body of the post from the WSS adapter";  
  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Category</PropertyName1>  
<PropertySource1>” + int_Category + “</PropertySource1>  
<PropertyName2>Published</PropertyName2>  
<PropertySource2>” + str_Published + “</PropertySource2>  
<PropertyName3>Title</PropertyName3>  
<PropertySource3>” + str_Title + “</PropertySource3>  
<PropertyName4>Body</PropertyName4>  
<PropertySource4>” + str_Body + “</PropertySource4>  
</ConfigPropertiesXml>”;  
```  
  
 Les variables dans cette expression utilisent les types suivants :  
  
|Nom de la variable|Type|  
|-------------------|----------|  
|int_Category|System.Int32|  
|str_Published|System.String|  
|str_Title|System.String|  
|str_Body|System.String|  
  
 Un message ainsi créé sera défini à l’état **ne pas approuvées**, ce qui nécessitera une approbation par le propriétaire du blog avant qu’il soit visible sur le site.  
  
 Les types de colonne pris en charge pour la liste peuvent être affichés dans la page Paramètres de la liste. Pour plus d’informations sur les types de colonne Windows SharePoint Services qui sont pris en charge par l’adaptateur Windows SharePoint Services, consultez [référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md).  
  
## <a name="sending-to-and-receiving-from-a-windows-sharepoint-services-40-wiki-document-library"></a>Envoi à et réception d'une bibliothèque de documents Wiki Windows SharePoint Services 4.0  
 Dans un site Windows SharePoint Services 4.0, un site Wiki utilise la **Pages Wiki** bibliothèque de documents. La bibliothèque de documents Pages Wiki stocke le texte de la page Wiki dans une **contenu Wiki** colonne qui utilise un type d’interface utilisateur **plusieurs lignes de texte**. Le **plusieurs lignes de texte** type d’interface utilisateur est en corrélation avec la **SPFieldType.Note** le type de modèle d’objet SharePoint. Pour plus d’informations sur les types de colonne Windows SharePoint Services qui sont pris en charge par l’adaptateur Windows SharePoint Services, consultez [référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md).  
  
### <a name="sending-to-a-windows-sharepoint-services-40-wiki-document-library"></a>Envoi à une bibliothèque de documents Wiki Windows SharePoint Services 4.0  
 Lors de l’envoi des messages à un site Wiki Windows SharePoint Services 4.0, le contenu de la page Wiki est stocké dans la propriété de contexte de l’adaptateur Windows SharePoint Services nommée **WSS. ConfigPropertiesXml**. Pour publier un message sur un site Wiki Windows SharePoint Services 4.0, entrez les valeurs suivantes dans l’adaptateur **propriétés du Transport** boîte de dialogue lors de la configuration d’un port d’envoi qui utilise l’adaptateur Windows SharePoint Services :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|URL Dossier de destination|URL de la page d'accueil du site Wiki, relative au site SharePoint, par exemple « wikiSP ».|  
|URL de site SharePoint|URL du site Wiki Windows SharePoint Services 4.0, par exemple http://*\<nom_serveur >*/sites/wiki/où  *\<nom_serveur >* est un espace réservé pour le nom réel du serveur web.|  
  
 La valeur pour le **contenu Wiki** propriété pour la page Wiki en définissant la valeur correspondante dans le fichier WSS. Propriété de contexte ConfigPropertiesXml du message. Cela est possible avec un pipeline personnalisé ou dans une orchestration. Par exemple, l'expression suivante dans une orchestration définit des valeurs dans la propriété de contexte WSS.ConfigPropertiesXml du message Message_Out.  
  
```  
str_Wiki = "This is a sample Wiki page entry.";  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  
  
 Utilisez la variable str_Wiki dans cette expression la **System.String** type de données.  
  
> [!IMPORTANT]
>  La bibliothèque de documents Wiki Windows SharePoint Services 4.0 prend en charge le contrôle de version, mais l'adaptateur Windows SharePoint Services pour BizTalk Server 2010 ne le prend pas en charge. Par conséquent, les pages Wiki mises à jour par l'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] perdent leurs versions précédentes. Du fait de cette limitation, une page Wiki reçue par l'adaptateur Windows SharePoint Services pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] et archivée dans une bibliothèque de documents Wiki différente conserve uniquement sa dernière version, toutes les autres versions étant supprimées.  
  
### <a name="receiving-from-a-windows-sharepoint-services-40-wiki-document-library"></a>Réception d'une bibliothèque de documents Wiki Windows SharePoint Services 4.0  
 Lors de la réception des messages à partir d’un site Wiki Windows SharePoint Services 4.0, le contenu de la page Wiki est stocké dans la propriété de contexte de l’adaptateur Windows SharePoint Services nommée **WSS. InPropertiesXml**.  
  
 Pour recevoir un message à partir d’une page Wiki Windows SharePoint Services 4.0, entrez les valeurs suivantes dans l’adaptateur **propriétés du Transport** boîte de dialogue lors de la configuration d’un emplacement de réception qui utilise l’adaptateur Windows SharePoint Services :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|URL de site SharePoint|URL de la page d'accueil du site Wiki, relative au site SharePoint, par exemple « wiki ».|  
|URL bibliothèque documents source|URL de la page d'accueil du site Wiki, relative au site SharePoint, par exemple « wikiRL ».|  
  
 Puis d’extraire le contenu de la page wiki le **contenu Wiki** nœud de la **WSS. InPropertiesXml** propriété de contexte du message reçu. Cela est possible avec un pipeline personnalisé ou dans une orchestration. Par exemple, dans l’expression suivante de l’orchestration, le **str_Wiki** variable est remplie avec la valeur de la **contenu Wiki** nœud à partir de la **WSS. InPropertiesXml** propriété de contexte de la **Message_In** message. Ensuite, la **contenu Wiki** propriété de la **WSS. ConfigPropertiesXml** propriété de contexte de la **Message_Out** message est défini à la valeur de la **str_Wiki** variable :  
  
```  
str_PropertiesXml = Message_In(WSS.InPropertiesXml);  
doc = doc.LoadXml(str_PropertiesXml);  
node = doc.SelectSingleNode("InPropertiesXml/Property[@name='Wiki Content']);  
str_Wiki = node.InnerText;  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  
  
 Les variables dans cette expression utilisent les types suivants :  
  
|Nom de la variable|Type|  
|-------------------|----------|  
|str_PropertiesXml|System.Xml.XmlDocument|  
|doc|System.Xml.XmlDocument|  
|node|System.Xml.XMLNode|  
|str_Wiki|System.String|  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter.md)