---
title: "Vue d’ensemble de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: adapters, overview
ms.assetid: 2d078b13-d41f-476f-bfb4-82be4d35a769
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3031bdf1317d96f64f1ea247c6f8cbf83e1688c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="overview-of-the-sap-adapter"></a>Vue d’ensemble de l’adaptateur SAP
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] expose le système SAP comme un service WCF. Les clients de carte peuvent effectuer des opérations sur le système SAP en échangeant des messages SOAP avec l’adaptateur. L’adaptateur utilise le message WCF et appelle approprié au système SAP pour effectuer l’opération. L’adaptateur retourne la réponse du système SAP au client sous la forme des messages SOAP.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] des métadonnées de surfaces d’artefacts SAP (RFC, BAPI, IDOC) qui décrivent la structure d’un protocole SOAP du message sous la forme de WSDL. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour permettre aux clients d’adaptateur récupérer des métadonnées pour les opérations et génère des artefacts de programmation qui peuvent être utilisés dans votre solution de programmation. Pour plus d’informations sur [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise la bibliothèque Unicode RFC, librfc32u.dll, pour communiquer avec le système SAP, outre l’utilisation d’autres DLL de prise en charge. Pour obtenir une liste complète des DLL SAP qui nécessite de l’adaptateur, consultez le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] guide d’installation. Le guide d’installation est généralement installé sur \<lecteur d’installation :\>\Program Files\\[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents. Vous pouvez utiliser la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour communiquer avec le système SAP, comme suit :  
  
-   En développant des applications BizTalk. Consultez [développement d’Applications BizTalk Server](../../core/developing-biztalk-server-applications.md) pour plus d’informations.  
  
-   À l’aide de la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service. Consultez [applications SAP de développer à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).
  
-   À l’aide du modèle de canal WCF. Consultez [applications SAP de développer à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment l’adaptateur effectue la connexion à un système SAP ?](https://msdn.microsoft.com/library/cc185540.aspx)  
  
-   [Quels sont les métadonnées d’adaptateur SAP Surface ?](https://msdn.microsoft.com/library/dd788039.aspx)  
  
-   [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/dd788159.aspx)  
  
-   [Autres fonctionnalités prises en charge par l’adaptateur](https://msdn.microsoft.com/library/dd788022.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)