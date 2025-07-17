# HAKIZA-Indicator
---

The HAKIZA-Indicator is a tool that can be used to geometrically visualize the **emergent, verifiable structures used in the MMB** via the metatrader (MT5).

### Key Features

1. **Alternating Highs and Lows**:
   - The `expecting_high` variable ensures that the zigzag alternates between marking highs and lows.
   - When `expecting_high` is `true`, the next reversal marks a **high**.
   - When `expecting_high` is `false`, the next reversal marks a **low**.

2. **Disconnected Zigzag Points**:
   - The zigzag buffer (`ZigzagBuffer[]`) only stores values at reversal points.
   - Non-reversal points are explicitly set to `EMPTY_VALUE`, ensuring no lines are drawn between them.

3. **Infinite Zigzag Pattern**:
   - By alternating between highs and lows, the zigzag points form a consistent up-and-down pattern when **imaginary connected**.

4. **Subwindow Placement**:
   - The `#property indicator_separate_window` directive places the indicator in a separate subwindow below the main chart.

---

### How It Works in the Subwindow
- The indicator will display **disconnected zigzag points** in the subwindow.
- Each point alternates between a **high** and a **low**, forming a consistent infinite zigzag pattern when imaginary connected.
- When there is no reversal, no point is drawn, creating a "break" in the sequence.

---

### Customization Options
1. **Colors**:
   - Change the `indicator_color1` property to customize the color of the zigzag points.

2. **Point Style**:
   - You can modify the appearance of the points (e.g., dots, crosses) by using `SetIndexStyle()` in the `OnInit()` function. For example:
     ```mql5
     SetIndexStyle(0, DRAW_ARROW);
     SetIndexArrow(0, 159); // Use a specific arrow style
     ```

3. **Alerts**:
   - Add alerts when a reversal is detected by including `Alert()` or `SendNotification()` in the reversal detection logic.

---

### Testing the Indicator
1. Copy the code into the MetaEditor in MT5.
2. Compile the code to generate the indicator file (`.ex5`).
3. Attach the indicator to your chart. It will appear in a separate subwindow below the main chart, showing disconnected zigzag points that alternate between highs and lows.
