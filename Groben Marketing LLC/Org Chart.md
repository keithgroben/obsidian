# Org Chart

*Source: Notion — https://www.notion.so/2e26abe00ba480ccb81ec14ddfd284f7 (YG Docs · Tags: Team)*

*(Originally a Yoder Graphics org chart — routed to GM LLC per user instruction)*

> Need to get a full list of 'departments' and role responsibilities before completing.

```mermaid
flowchart TB
    MARC["<b>MARC</b><br>President"]

    subgraph REV["1. REVENUE & GROWTH"]
        KEITH["<b>KEITH</b><br>Director of Sales & Marketing"]
        subgraph MKT_BOX["Marketing"]
            MKT_DEPT["<b>Marketing Dept</b><br>Lead Gen & Content"]
        end
        subgraph SALES_BOX["Sales"]
            SALES_DEPT["<b>Sales Dept</b><br>Account Executives"]
            EST_DEPT["<b>Estimating</b><br>Technical Pricing"]
            SALES_DEPT --> EST_DEPT
        end
        KEITH --> MKT_BOX
        KEITH --> SALES_BOX
    end

    subgraph PROJ["2. PROJECT SERVICES"]
        subgraph CREATIVE_BOX["Creative"]
            MARCY["<b>MARCY</b><br>Creative Director"]
            GRAPHICS["<b>Graphic Designers</b><br>Production Art"]
            MARCY --> GRAPHICS
        end
        subgraph PROCURE_BOX["Procurement"]
            TAMI["<b>TAMI</b><br>Vendor Manager"]
            ORDER["<b>Order Processing</b><br>Outsource Logistics"]
            TAMI --> ORDER
        end
    end

    subgraph OPS["3. OPERATIONS"]
        JAMIE["<b>JAMIE</b><br>Operations Manager"]
        subgraph PROD_BOX["Fabrication"]
            KIRK["<b>KIRK</b><br>Production Lead"]
            PROD_FN["<b>Production Floor</b><br>- Print Production<br>- Sign Fabrication"]
            KIRK --> PROD_FN
        end
        subgraph INST_BOX["Installation"]
            OPEN_INST["<b>OPEN ROLE</b><br>Install Manager"]
            INST_FN["<b>Installation Team</b><br>- Vehicle Wraps<br>- On-Site Install"]
            OPEN_INST --> INST_FN
        end
        subgraph FULF_BOX["Fulfillment"]
            JAMIE_ACT["<b>JAMIE (Acting)</b><br>Fulfillment Lead"]
            FULFILL_FN["<b>Fulfillment Team</b><br>- Pack & Ship<br>- Delivery"]
            JAMIE_ACT --> FULFILL_FN
        end
        JAMIE --> PROD_BOX
        JAMIE --> INST_BOX
        JAMIE --> FULF_BOX
    end

    subgraph ADMIN["4. ADMIN & SUPPORT"]
        subgraph OFFICE_BOX["Office Operations"]
            NEW_HIRE["<b>OPEN ROLE</b><br>Office Administrator"]
            OFFICE_FN["<b>Office Functions</b><br>- Logistics & Sched.<br>- HR Support<br>- AP/AR Prep"]
            NEW_HIRE --> OFFICE_FN
        end
    end

    MARC --> REV
    MARC --> PROJ
    MARC --> OPS
    MARC --> ADMIN
```
