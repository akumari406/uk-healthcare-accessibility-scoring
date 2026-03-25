# Accessibility Features Framework

This document defines the set of features used to evaluate the accessibility of healthcare facilities in the UK for disabled populations. Features are grouped into two main categories:

- Travel Route Features
- Facility Features

Each feature includes:
- Data source(s)
- Relevant regulation or standard
- Method used for extraction or modelling
- Data collection approach

---

## 1. Travel Route Features

| Feature | Data Source(s) | Regulation / Standard | AI / Data Method | Collection Method |
|--------|----------------|----------------------|------------------|------------------|
| Distance to nearest bus stop | London Datastore (GLA), OSM | Equality Act (indirect), BS 8300 | Nearest-neighbour spatial analysis | API + GIS |
| Distance to nearest tube station | London Datastore (GLA), OSM | Equality Act (indirect) | Network distance calculation | API + GIS |
| Distance to nearest accessible tube station | TfL / GLA datasets | Equality Act | Filtered proximity analysis (step-free only) | API |
| Public Transport Accessibility Level (PTAL) | London Datastore (GLA) | Planning guidance | Spatial overlay analysis | API |
| Step-free public transport connectivity | TfL / GLA datasets | Equality Act | Network accessibility modelling | API |
| Walking time to nearest transport node | OSM, OS OpenMap | BS 8300 | Isochrone modelling | GIS |
| Step-free route to entrance | OSM, OS OpenMap, NHS websites | Part M, BS 8300-1 | Network analysis | API + GIS + scraping |
| Ramp gradients & landings | OS/EA Elevation, OSM | Part M, BS 8300 | Slope analysis | GIS |
| Dropped kerbs | OSM, Local authority data | Part M, BS 8300 | Tag extraction | API |
| Tactile paving | OSM, Local datasets | Part M, BS 8300 | Tag parsing / CV | API |
| Hazard protection (external routes) | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Patient drop-off points | NHS websites, OSM | Part M, BS 8300 | NLP + POI detection | Scraping + API |
| External route widths | OS OpenMap | BS 8300 | Spatial measurement | GIS |
| Passing places (external) | OS OpenMap | BS 8300 | Spatial detection | GIS |
| External gradients | OS/EA Elevation | BS 8300 | Terrain modelling | GIS |
| Step-free network continuity | OS, OSM, GLA | Equality Act | Accessibility routing algorithm | API + GIS |
| Accessible principal entrance | NHS websites, OSM | Part M, BS 8300 | NLP + classification | Scraping + API |
| Door clear widths | NHS websites | Part M | NLP numeric extraction | Web scraping |
| Lobby dimensions | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Automatic doors | NHS websites | BS 8300 | NLP classification | Web scraping |
| Access control heights | NHS websites | BS 8300 | NLP + inference | Web scraping |
| Corridor widths | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Passing spaces (internal) | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Turning circles | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Slip-resistant flooring | NHS websites | BS 8300 | NLP classification | Web scraping |
| Passenger lifts | NHS websites | Part M | NLP extraction | Web scraping |
| Lift dimensions | NHS websites | BS 8300 | NLP numeric parsing | Web scraping |
| Lift lobby space | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Stair geometry | NHS websites | Part M | NLP extraction | Web scraping |
| Handrails | NHS websites | Part M | NLP classification | Web scraping |
| Nosing contrast | NHS websites | Part M | NLP classification | Web scraping |

---

## 2. Facility Features

| Feature | Data Source(s) | Regulation / Standard | AI / Data Method | Collection Method |
|--------|----------------|----------------------|------------------|------------------|
| Accessible parking bays | NHS websites, OSM | Part M, BS 8300 | NLP + POI extraction | Scraping + API |
| Parking dimensions & transfer zones | NHS websites | BS 8300 | NLP numeric extraction | Web scraping |
| Ambulance drop-off areas | NHS websites | Healthcare guidance | NLP classification | Web scraping |
| Mobility scooter provision | NHS websites | BS 8300 | NLP classification | Web scraping |
| Accessible WC | NHS websites | Part M | NLP extraction | Web scraping |
| Ambulant WC | NHS websites | Part M | NLP extraction | Web scraping |
| Changing Places facility | NHS websites | BS 8300 | NLP keyword detection | Web scraping |
| Accessible showers | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Level access showers | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Hoist systems | NHS websites | BS 8300 | NLP classification | Web scraping |
| WC layout (turning space) | NHS websites | BS 8300 | NLP + rule validation | Web scraping |
| Basin height | NHS websites | BS 8300 | NLP numeric extraction | Web scraping |
| WC seat height | NHS websites | BS 8300 | NLP numeric extraction | Web scraping |
| Accessible bedrooms | NHS websites | BS 8300 | NLP classification | Web scraping |
| Bed transfer space | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Bed clearance zones | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Accessible en-suite bathrooms | NHS websites | BS 8300 | NLP classification | Web scraping |
| Reception counter height | NHS websites | Part M | NLP extraction | Web scraping |
| Dual-height counters | NHS websites | BS 8300 | NLP classification | Web scraping |
| Knee recess at counters | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Waiting area seating | NHS websites | BS 8300 | NLP extraction | Web scraping |
| Wheelchair spaces in waiting areas | NHS websites | Part M | NLP extraction | Web scraping |
| Reach range ergonomics | NHS websites | BS 8300 | NLP + validation | Web scraping |
| Control heights | NHS websites | Part M | NLP numeric extraction | Web scraping |
| Nurse call systems | NHS websites | Healthcare guidance | NLP classification | Web scraping |

---

## Appendix A: Notes and Definitions

**A1. Accessibility Standards**
- *Part M*: UK Building Regulations for access to and use of buildings  
- *BS 8300*: British Standard for inclusive design of the built environment  
- *Equality Act 2010*: Legal framework ensuring non-discrimination  

**A2. Spatial Methods**
- *Nearest-neighbour analysis*: Identifies closest facility using geometric distance  
- *Network analysis*: Uses real-world paths (roads, pavements) instead of straight-line distance  
- *Isochrone modelling*: Estimates reachable areas within a given travel time  
- *Accessibility routing*: Evaluates routes based on constraints (e.g., step-free paths)

**A3. AI / Data Methods**
- *NLP (Natural Language Processing)*: Extracts structured information from text (e.g., NHS webpages)  
- *POI detection*: Identifies physical features such as entrances or parking  
- *Computer Vision (CV)*: Detects features like tactile paving (where applicable)  

**A4. Data Limitations**
- NHS website data may be incomplete or inconsistent  
- OSM coverage varies by location  
- Accessibility features may not always be explicitly documented

**A6. Public Transport Accessibility Level (PTAL)**  
PTAL is a UK-specific metric developed by Transport for London (TfL) to quantify how well a location is served by public transport. It combines:
- Walking time to nearby public transport access points (PTAPs)
- Service frequency and reliability

PTAL values are categorised from **0 (very poor accessibility)** to **6b (excellent accessibility)**.

In this research, PTAL is used as a **proxy for transport connectivity**, but it has important limitations:
- It does not account for **step-free access or physical barriers**
- It is primarily available for **London**, limiting nationwide consistency
- It does not reflect **user-specific accessibility needs** (e.g., wheelchair users)

Therefore, PTAL is used alongside additional features such as step-free routes and accessible stations to provide a more comprehensive accessibility assessment.

**A5. Interpretation Note**
Not all features contribute equally to accessibility. Weighting and aggregation methods are defined separately in the scoring model.

---
