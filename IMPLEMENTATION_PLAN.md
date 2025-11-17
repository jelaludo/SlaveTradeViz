# Implementation Plan: Dimensional Metadata & Filtering System

## Overview
Add dimensional metadata to all slavery systems to enable filtering, comparison, and visual encoding by dimensions rather than just by trade type.

## Phase 1: Data Structure Updates ✅

### Task 1.1: Add dimension metadata to all 14 systems
- [ ] Roman Empire
- [ ] Chinese & Korean Internal Slavery
- [ ] Pre-Columbian American Slavery
- [ ] Trans-Saharan Slave Trade
- [ ] Slavic Slave Trade
- [ ] Southeast Asian Slave Systems
- [ ] Mongol & Steppe Imperial Enslavement
- [ ] Devshirme (Ottoman Child Levy) - verify existing
- [ ] Crimean/Black Sea
- [ ] Indian Ocean Trade
- [ ] Barbary Corsairs
- [ ] Red Sea Trade
- [ ] Transatlantic Trade
- [ ] Modern Slavery

**Data structure for each:**
```javascript
{
  acquisition_mode: ["war_captive", "raid", ...],  // Array of strings
  legal_status: ["chattel_property", ...],          // Array of strings
  labor_types: ["military", "domestic_household", ...], // Array of strings
  brutality_profile: {
    transport_mortality: 0-3,
    bodily_mutilation: 0-3,
    sexual_exploitation: 0-3,
    hereditary_rigidity: 0-3,
    upward_mobility: 0-3  // inverted: 3 = best
  }
}
```

**Source**: `Slavery_Viz_Dimensions_ Values.md`

---

## Phase 2: UI Components

### Task 2.1: Create Filter Modal Component
**Location**: Top of page, toggleable button

**Components needed:**
- [ ] Filter button/icon in header
- [ ] Modal overlay with filter panels
- [ ] Acquisition Mode checkboxes (multi-select, OR logic)
- [ ] Legal Status checkboxes (multi-select, OR logic)
- [ ] Labor Types checkboxes (multi-select, OR logic)
- [ ] Brutality Profile sliders (0-3 scale for each dimension)
- [ ] Apply/Reset buttons
- [ ] Active filter indicator chips

**Filter Logic:**
- Within each dimension: OR (any selected matches)
- Across dimensions: AND (all selected dimensions must match)
- Sliders: minimum threshold (show systems ≥ selected value)

### Task 2.2: Create Brutality Legend Component
**Location**: Sidebar or below treemap

**Components needed:**
- [ ] Legend container with title
- [ ] Scale visualization (0-3 chips with labels)
- [ ] Dimension descriptions (dl/dt/dd structure)
- [ ] Special note for upward_mobility inversion

**HTML Structure** (provided by user):
```html
<div class="legend brutality-legend">
  <h3>Brutality Dimensions (0–3 Scale)</h3>
  <div class="legend-scale">...</div>
  <dl class="legend-dimensions">...</dl>
</div>
```

### Task 2.3: Color-by-Dimension Toggle
- [ ] Toggle button: "Color by Trade" / "Color by Dimension"
- [ ] Dropdown to select which dimension to color by
- [ ] Color scale generator (blue→red for brutality, distinct colors for categories)

---

## Phase 3: Filtering Logic

### Task 3.1: Filter State Management
- [ ] React state for filters:
  ```javascript
  const [filters, setFilters] = useState({
    acquisition: [],
    legalStatus: [],
    laborTypes: [],
    brutality: {
      transport_mortality: 0,
      bodily_mutilation: 0,
      sexual_exploitation: 0,
      hereditary_rigidity: 0,
      upward_mobility: 0
    }
  });
  ```

### Task 3.2: Filter Function
- [ ] `filterTrades(trades, filters)` function
- [ ] OR logic within dimensions
- [ ] AND logic across dimensions
- [ ] Slider threshold logic (≥ value)

### Task 3.3: Integration Points
- [ ] Update `drawVisualization()` to use filtered data
- [ ] Update `drawTreemap()` to use filtered data
- [ ] Re-render on filter changes

---

## Phase 4: Visual Encoding

### Task 4.1: Color-by-Dimension System
- [ ] Color scale for brutality dimensions (0=blue, 3=red)
- [ ] Color mapping for categorical dimensions (acquisition, legal status, labor types)
- [ ] Update node and flow colors based on selected dimension

### Task 4.2: Visual Feedback
- [ ] Fade out filtered systems (reduced opacity)
- [ ] Highlight matching systems
- [ ] Show filter count indicator

---

## Phase 5: CSS Styling

### Task 5.1: Filter Modal Styles
- [ ] Modal overlay (dark background, centered)
- [ ] Filter panel layout (grid or flex)
- [ ] Checkbox and slider styling
- [ ] Button styling (Apply/Reset/Close)

### Task 5.2: Legend Styles
- [ ] Legend container styling
- [ ] Scale chip colors (level-0 through level-3)
- [ ] Dimension list styling (dl/dt/dd)
- [ ] Responsive layout

### Task 5.3: Filter Indicator Styles
- [ ] Active filter chips
- [ ] Remove filter button (X icon)
- [ ] Filter count badge

---

## Phase 6: Testing & Verification

### Task 6.1: Data Verification
- [ ] Verify all 14 systems have complete dimension data
- [ ] Verify Devshirme dimensions match provided values
- [ ] Check data consistency (no missing fields)

### Task 6.2: Filter Testing
- [ ] Test each filter type independently
- [ ] Test combined filters (multiple dimensions)
- [ ] Test slider thresholds
- [ ] Test edge cases (no filters, all filters)

### Task 6.3: Visual Testing
- [ ] Test color-by-dimension toggle
- [ ] Test filter visual feedback (fade/highlight)
- [ ] Test responsive layout
- [ ] Test modal interactions

---

## Implementation Order

1. **Phase 1** - Data structure (foundation)
2. **Phase 2.2** - Legend component (static, no logic)
3. **Phase 3** - Filtering logic (core functionality)
4. **Phase 2.1** - Filter modal UI (wires into logic)
5. **Phase 4** - Visual encoding (enhancement)
6. **Phase 5** - CSS styling (polish)
7. **Phase 6** - Testing (verification)

---

## Notes

- **Filter Logic**: OR within dimensions, AND across dimensions
- **Color Scale**: Blue→Red for brutality (0=blue, 3=red)
- **Modal**: Click to reveal, overlay with close button
- **Legend**: Static explanation, always visible
- **Devshirme**: Already in code, verify dimensions match provided values

