# Client Status Update Webhook

This document lists the **event types** a client webhook may receive from Shopini Express.  
In each payload, the event identifier appears in the `type` field.

---

## Domestic Shipments — Supported Events

| Event key | When it fires |
|---|---|
| `accept` | When the consignment is out for delivery |
| `added_to_bag` | When the consignment is added to a bag in a trip |
| `assigned_for_delivery` | When a consignment is assigned to any rider for delivery |
| `assigned_to_hub` | When task is assigned to rider for delivery |
| `attempted` | When a consignment is undelivered |
| `bag_received` | When bag is unloaded from the trip |
| `cancelled` | When a consignment is cancelled |
| `consignment_verification` | When consignment verification is done |
| `customs_clearance_completed` | When the consignment is cleared from customs |
| `delay_at_airport` | When the consignment is at airport and not processed due to some reasons |
| `delivered` | When a consignment is delivered |
| `delivery_pod` | When the 3PL sends POD separately after the `delivered` event |
| `deps_exception` | When the consignment is received as Damaged, Excess, Shortage or Pilferage |
| `exception` | When an event is received that does not belong to other events in the list |
| `handed_in_customs_clearance` | When the consignment is handed to the customs at airport |
| `handover_courier_partner` | When the consignment is handed over to the 3PL |
| `inscan_at_hub` | When a consignment is in-scanned at any hub |
| `intransittohub` | When a consignment is part of a mid-mile hub and the mid-mile trip is ongoing |
| `lost` | When a consignment is lost |
| `not_picked_up` | When the consignment is not picked up |
| `on_hold` | When a consignment is put on hold for some reasons |
| `out_for_pickup` | When the delivery executive is out for pickup |
| `out_for_store_pickup` | When the delivery executive is out for pickup (PUDO flow only) |
| `outscan_at_hub` | When a consignment is marked as out-scan from a hub |
| `pickup_awaited` | When the delivery executive is yet to be assigned for pickup |
| `pickup_completed` | When the pickup is completed by the delivery executive |
| `pickup_scheduled` | When the pickup has been scheduled for a consignment |
| `reachedathub` | When the consignment reaches the destination hub (generally the last-mile hub) |
| `release_on_hold` | When a consignment is released from hold |
| `reschedule` | When the consignment pickup or delivery is rescheduled |
| `returned_at_hub` | When the consignment is received at hub post a delivery attempt |
| `revert_from_delivered` | When a consignment is revoked from delivery for exceptional reasons (CRM) |
| `revoke_rto` | When RTO is revoked for exceptional reasons (CRM) |
| `rto` | When the consignment is marked as RTO |
| `rto_attempted` | When the consignment is undelivered in an RTO journey |
| `rto_delivered` | When the consignment is delivered in an RTO journey |
| `rto_in_transit` | When the consignment is in transit in an RTO journey |
| `rto_initiated` | When the consignment is marked as RTO (preferred over `rto`) |
| `rto_inscan_at_hub` | When the consignment is in-scanned at hub in an RTO journey |
| `rto_outfordelivery` | When the consignment is out for delivery in an RTO journey |
| `seized` | When the consignment is seized by an external party before delivery |
| `shelved` | When the consignment is shelved for some reasons |
| `softdata_upload` | When the consignment is created in the Shipsy system |
| `vehicle_arrived` | When the vehicle has arrived at a different hub in a middle-mile trip |

> **Note:** Some event keys are intentionally kept as provided (`intransittohub`, `reachedathub`) even if they appear inconsistent. Use them exactly as listed when matching on `type`.

---

## Cross Border Shipments — Supported Events

| Event key | When it fires |
|---|---|
| `on_hold` | Consignment is put on hold |
| `release_on_hold` | Consignment is released from hold |
| `pickup_completed` | Pickup is completed |
| `delivered` | Consignment is delivered |
| `attempted` | Consignment is undelivered |
| `rto` | Consignment is marked as RTO |
| `cancel` | Consignment is cancelled |
| `shipment_clear_successfully` | Shipment is cleared successfully |
| `intransit_to_hub` | Consignment is in transit to a hub |
| `reached_at_hub` | Consignment has reached a hub |
| `inscan_at_hub` | Consignment is in-scanned at hub |
| `accept` | Consignment is out for delivery |

---

## Example (payload shape – illustrative)

> The actual webhook payload from Shopini Express will include `type` and additional fields.  
> This example is **illustrative only** to show where `type` appears.

```json
{
  "type": "delivered",
  "tracking_number": "TRK12345",
  "occurred_at": "2024-02-20T10:09:33Z",
  "data": {
    "notes": null
  }
}
