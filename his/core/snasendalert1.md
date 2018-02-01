---
title: "SNASendAlert1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ee39476-cc38-4381-bed9-6af5d01fe17b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNASendAlert
The SNALink calls the **SNASendAlert** function to send a complete preformatted Network Management Vector Transport (NMVT) alert to NetView.  
  
```  
VOID SNASendAlert(  
PTRBFHDR msgptr,  
INTEGER severity  
);  
```  
  
## Parameters  
 *msgptr*  
 Pointer to the NMVT alert to be sent.  
  
 *severity*  
 The severity of the problem that caused the alert (ranges from 0 through 16).  
  
## Remarks  
 The complete NMVT to be sent must be generated by the SNALink and inserted into a buffer. Only the elements are used—the buffer header need not be set up before sending. The fields **startd** and **endd** should be set to reflect the location of the NMVT within the element. Multiple elements can be used to store the NMVT, up to a maximum length of 512 bytes. The buffer will be freed by the Base after the NMVT has been sent.  
  
 Any NMVT sent refers to a particular Host Integration Server connection. It is recommended that the NMVT include at least a hierarchy resource list, giving the name of the remote physical unit (PU) that the connection is associated with. This name is supplied to the SNALink on the [Open(STATION)](../core/open-station-1.md) message.  
  
 For complete details of the format of an NMVT, see the IBM manual *SNA Formats* (GA27-3136).