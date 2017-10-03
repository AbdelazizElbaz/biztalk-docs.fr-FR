---
title: "Comment modifier le comportement d’une Interface de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4a4946a-e345-4c7e-835d-a3f7f72ebaca
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a4bedc387b879d5ddf21197e3dec4470f2e9b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-behavior-of-a-single-sign-on-interface"></a>Modification du comportement d'une interface d'authentification unique
La plupart des objets du modèle d'authentification unique (SSO, Single Sign-On) de l'entreprise exposent l'interface IPropertyBag, qui permet de modifier le comportement de l'objet spécifié. Si vous appelez QueryInterface sur un objet SSO, vous pouvez accéder à l'interface IPropertyBag et l'utiliser pour changer le comportement de l'objet actif.  
  
### <a name="to-change-the-behavior-for-a-specified-sso-interface"></a>Pour modifier le comportement d'une interface SSO spécifiée  
  
1.  Utilisez QueryInterface sur l'interface spécifiée pour accéder à une instance IPropertyBag.  
  
2.  Utilisez IPropertyBag.Write pour définir la propriété, le type et la valeur de l'interface.  
  
     Le tableau ci-dessous décrit les valeurs valides pour les paramètres IPropertyBag propName et ptrVar.  
  
|propName|Type|ptrValue|Utilisable sur|  
|--------------|----------|--------------|---------------|  
|CurrentSSOServer|VT_BSTR|Nom du serveur auquel les informations doivent être envoyées|Tous|  
|Transaction|VT_UNKNOWN<br /><br /> VT_EMPTY|Pointeur ITransaction DTC ou NULL pour effacer l'étendue.|ISSOConfigStore::SetConfigInfo<br />ISSOConfigStore::GetConfigInfo <br />ISSOConfigStore::DeleteConfigInfo<br /><br /> ISSOAdmin::CreateApplication<br />ISSOAdmin::DeleteApplication <br />ISSOAdmin::UpdateApplication<br />ISSOAdmin::CreateFieldInfo<br /><br /> ISSOMapper::GetFieldInfo|  
|AppFilterFlags|VT_I4<br /><br /> VT_UI4|Indicateurs permettant de contrôler l'application à filtrer.|ISSOMapper::GetApplications<br /><br /> ISSOMapper2::GetApplications2|  
|AppFilterFlagsMask|VT_I4<br /><br /> VT_UI4|Masque d'indicateur permettant de contrôler l'application à filtrer.|ISSOMapper::GetApplications<br /><br /> ISSOMapper2::GetApplications2|  
|AsyncCall|VT_BOOL|True pour appeler via un RPC asynchrone. False pour utiliser un RPC synchrone.|ISSOConfigOM::GetServerStatus<br /><br /> ISSOAdmin::GetGlobalInfo|  
  
-   **CurrentSSOServer**: le comportement standard pour déterminer quel serveur pour envoyer les informations SSO est comme suit :  
  
    1.  Recherche de l'utilisateur actuel dans le registre. Le nom du serveur peut être défini pour l'utilisateur actuel à l'aide des outils de ligne de commande ou de l'interface graphique.  
  
    2.  Recherche de tous les utilisateurs dans le registre. Le nom du serveur peut être défini pour tous les utilisateurs à l'aide des outils de ligne de commande ou de l'interface graphique.  
  
    3.  Si aucun nom de serveur SSO n'est trouvé dans le registre, utilisez l'ordinateur en cours.  
  
     Le fait de définir CurrentSSOServer sur un serveur spécifique annule le processus précédent de l'interface spécifiée. Une fois la valeur CurrentSSOServer définie, tous les appels de méthode suivants liés à l'interface sont envoyés au serveur spécifié.  
  
-   **Transaction**: Spécifie une transaction DTC à étendue les opérations effectuées par l’authentification unique de l’objet modèle. Vous devez transmettre un pointeur ITransaction DTC dans `ptrValue` ou indiquer la valeur « null » pour effacer la portée de la transaction existante.  
  
-   **AppFilterFlags/AppFilterMask**: contrôle les types d’applications qui seront retournées à partir de ISSOMapper.GetApplications et ISSOMapper2.GetApplications. Si les indicateurs des applications correspondent aux indicateurs spécifiés par les indicateurs de filtre et le masque des indicateurs de filtre, ils sont retournés. Pour effectuer le filtrage d'applications, vous pouvez définir AppFilterFlagsMask sur SSO_FLAG_APP_FILTER_BY_TYPE, puis AppFilterFlags sur l'une ou plusieurs des valeurs suivantes :  
  
     SSO_APP_TYPE_INDIVIDUAL  
  
     SSO_APP_TYPE_GROUP  
  
     SSO_APP_TYPE_CONFIG_STORE  
  
     SSO_APP_TYPE_HOST_GROUP  
  
     SSO_APP_TYPE_PS_ADAPTER  
  
     SSO_APP_TYPE_PS_GROUP_ADAPTER  
  
-   **AsyncCall**: si la valeur est true, puis l’authentification unique effectue la méthode à l’aide d’un appel asynchrone de procédure distante (RPC). En cours d'exécution , la méthode retourne la valeur E_PENDING. Toute autre valeur retournée indique que la méthode est terminée. AsyncCall vous permet également de savoir si la méthode est terminée.