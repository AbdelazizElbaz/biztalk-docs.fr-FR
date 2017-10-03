---
title: Configuration du fichier XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52851901-8374-412f-9c29-83845d8d4861
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d791de9b6fe90ebb850874026e8d52e49732f32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-xml-file"></a>Configuration du fichier XML
Lorsque vous installez l'authentification unique de l'entreprise, un fichier XML intitulé ENTSSO.xml est installé dans le répertoire Extensions. En modifiant ce fichier, vous définissez la configuration pour toutes les instances d'agent de gestion ENTSSO.  
  
 Le fichier est semblable à ce qui suit :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<sso>  
  
  <SourceMA name="RACFMA1" objectType="person" attribute="uid"/>  
  <SourceMA name="ACF2" objectType="person" attribute="uid"/>  
  
  <ENTSSOMA name ="ENTSSOMA1" adma="ADMA1" deleteAll="true">  
    <Application name="AppForRACF1A" sourceMA="RACFMA1" create="true" delete="true"/>  
    <Application name="AppForRACF1B" sourceMA="RACFMA1" create="true" delete="false"/>  
  </ENTSSOMA>  
  
  <ENTSSOMA name ="ENTSSOMA2" adma="ADMA1" deleteAll="true">  
    <Application name="AppForACF2" sourceMA="ACF2"/>  
  </ENTSSOMA>  
  
</sso>  
```  
  
## <a name="xml-elements-and-attributes"></a>Éléments et attributs XML  
 La liste suivante répertorie les éléments et attributs que vous définissez dans le fichier XML. Notez que tous les noms des éléments et des attributs de ce fichier respectent la casse.  
  
 **Élément : ENTSSO** -définit la configuration d’une seule instance de l’agent de gestion ENTSSO. Plusieurs éléments ENTSSO sont autorisés.  
  
 **Attribut : nom** - définit le nom de l’instance de l’Agent de gestion ENTSSO et doit correspondre au nom de l’instance de l’Agent de gestion ENTSSO dans Microsoft Identity Integration Server (MIIS).  
  
 **Attribut : adma** -définit le nom de l’instance de l’Agent de gestion Active Directory qui sera utilisé par cette instance de l’Agent de gestion ENTSSO. L'agent de gestion Active Directory fournit le nom de domaine Windows et le nom d'utilisateur Windows pour le mappage. Le nom de cette instance d'agent de gestion Active Directory doit correspondre au nom d'une instance d'agent de gestion Active Directory dans MIIS.  
  
 **Attribut : deleteAll** - en option, valeur par défaut est `true`. S'il est défini sur `true` et qu'une identité Windows est supprimée, tous les mappages utilisant cette identité Windows sont supprimés des applications ENTSSO.  
  
 **Élément : Application de** -définit la relation entre une application associée SSO et un Agent de gestion externe. Plusieurs éléments `Application` sont autorisés.  
  
 **Attribut : nom** -définit le nom de l’application associée SSO. Cette application doit déjà exister au sein du système ENTSSO.  
  
 **Attribut : sourceMA** -définit le nom d’instance de la source (externe) de l’Agent de gestion qui permet de fournir l’ID d’utilisateur externe dans le mappage pour cette application. Le nom de l'instance d'agent de gestion externe doit correspondre à un nom d'agent de gestion externe dans MIIS.  
  
 **Attribut : création de** - en option, valeur par défaut est `true`. Il indique si des mappages doivent être créés pour cette application.  
  
 **Attribut : suppression de** - en option, valeur par défaut est `true`. Il indique si des mappages doivent être supprimés pour cette application.  
  
 **Élément : SourceMA** : facultatif. Il identifie les noms du type d'objet et de l'attribut pour une instance d'agent de gestion source (externe) spécifique. Si cet élément n'est pas présent pour un agent de gestion spécifique, le type d'objet et les noms des attributs par défaut (respectivement « person » et « uid ») sont utilisés. Plusieurs éléments `SourceMA` sont autorisés.  
  
 **Attribut : nom** -le nom de la source (externe) de l’Agent de gestion. Le nom doit correspondre au moins à l'un des noms d'attributs `sourceMA` à partir des éléments `Application`.  
  
 **Attribut : objectType** - en option, valeur par défaut est `person`. Si le nom du type d'objet qui fournit l'UserId externe ne correspond pas à `person`, vous devez le spécifier ici.  
  
 **Attribut : attribut** - en option, valeur par défaut est `uid`. Si le nom de l'attribut qui fournit l'UserId externe ne correspond pas à `uid`, vous pouvez le spécifier ici.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de l’Agent de gestion ENTSSO](../core/how-to-use-the-entsso-management-agent.md)