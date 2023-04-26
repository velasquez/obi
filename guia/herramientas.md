---
layout: page
title: Herramientas
subtitle: Para confirmar bloqueos
---

Teniendo una idea del tipo de bloqueo al que nos enfrentamos podemos usar diferentes herramientas que miden diferentes situaciones para confirmar el bloqueo que estamos investigando. En esta sección haremos énfasis en dos herramientas públicas: IOADA y OONI.

Un concepto básico que debemos tener en cuenta a la hora de hacer estas investigaciones son los ASs o Sistemsa Autónomos (Autonomous systems).

### Qué es un AS?

Un **Sistema Autónomo** es un conjunto de direcciones IP que generalmente pertenecen a una empresa o ISP. Denotan un segmento de de red en internet. En el conexto de los bloqueos de internet es importante encontrar los ASNs que presentan bloqueos para poder documentarlos y atribuirlos.

Páginas como [ipinfo.io](https://www.ipinfo.io) nos pueden mostrar a que ASN pertenece una dirección ip. Este dato nos nos sirve a la hora de hacer búsquedas en las plataformas que describiremos a continuación.




## IODA (Internet Outage Detection and Analysis)

sitio web: https://ioda.inetintel.cc.gatech.edu/

IODA es un sistema de deteccion y análisis de caidas de internet que funcionan de una forma _macro_. Se pueden hacer análisis por rangos de fechas para paises, regiones o ASNs (Autonomous systems). 

IODA hace prubas constantes de la conectividad de redes al rededor del mundo de forma activa y pasiva y traduce los datos que colecta en un tablero de control que nos permite, de forma gráfica, confirmar caidas de internet en paises, regiones o ASNs.

