// Popover.tsx
import React, { useRef } from "react";
import {
  useRect,
  isHoriz,
  bestPositionOf,
  isOutsideX,
  isOutsideY,
  getWindow,
  getPadding
} from "@reactour/utils";

// styles.tsx
var defaultStyles = {
  popover: () => ({
    position: "fixed",
    maxWidth: 353,
    backgroundColor: "#fff",
    padding: "24px 30px",
    boxShadow: "0 0.5em 3em rgba(0, 0, 0, 0.3)",
    color: "inherit",
    zIndex: 1e5,
    transition: "transform 0.3s",
    top: 0,
    left: 0
  })
};
function stylesMatcher(styles) {
  return (key, state) => {
    const base = defaultStyles[key](state);
    const custom = styles[key];
    return custom ? custom(base, state) : base;
  };
}

// Popover.tsx
var Popover = ({
  children,
  position: providedPosition = "bottom",
  padding = 10,
  styles = {},
  sizes,
  refresher,
  ...props
}) => {
  const helperRef = useRef(null);
  const positionRef = useRef("");
  const verticalAlignRef = useRef("");
  const horizontalAlignRef = useRef("");
  const { w: windowWidth, h: windowHeight } = getWindow();
  const getStyles = stylesMatcher(styles);
  const helperRect = useRect(helperRef, refresher);
  const { width: helperWidth, height: helperHeight } = helperRect;
  const targetLeft = sizes == null ? void 0 : sizes.left;
  const targetTop = sizes == null ? void 0 : sizes.top;
  const targetRight = sizes == null ? void 0 : sizes.right;
  const targetBottom = sizes == null ? void 0 : sizes.bottom;
  const position = providedPosition && typeof providedPosition === "function" ? providedPosition(
    {
      width: helperWidth,
      height: helperHeight,
      windowWidth,
      windowHeight,
      top: targetTop,
      left: targetLeft,
      right: targetRight,
      bottom: targetBottom,
      x: sizes.x,
      y: sizes.y
    },
    helperRect
  ) : providedPosition;
  const available = {
    left: targetLeft,
    right: windowWidth - targetRight,
    top: targetTop,
    bottom: windowHeight - targetBottom
  };
  const [px, py] = getPadding(padding);
  const couldPositionAt = (position2) => {
    return available[position2] > (isHoriz(position2) ? helperWidth + px * 2 : helperHeight + py * 2);
  };
  const autoPosition = (coords) => {
    const positionsOrder = bestPositionOf(available);
    for (let j = 0; j < positionsOrder.length; j++) {
      if (couldPositionAt(positionsOrder[j])) {
        positionRef.current = positionsOrder[j];
        return coords[positionsOrder[j]];
      }
    }
    positionRef.current = "center";
    return coords.center;
  };
  const pos = (helperPosition) => {
    if (Array.isArray(helperPosition)) {
      const isOutX = isOutsideX(helperPosition[0], windowWidth);
      const isOutY = isOutsideY(helperPosition[1], windowHeight);
      positionRef.current = "custom";
      return [
        isOutX ? windowWidth / 2 - helperWidth / 2 : helperPosition[0],
        isOutY ? windowHeight / 2 - helperHeight / 2 : helperPosition[1]
      ];
    }
    const hX = isOutsideX(targetLeft + helperWidth, windowWidth) ? targetRight - helperWidth + px : targetLeft - px;
    const x = hX > px ? hX : px;
    const hY = isOutsideY(targetTop + helperHeight, windowHeight) ? targetBottom - helperHeight + py : targetTop - py;
    const y = hY > py ? hY : py;
    if (isOutsideY(targetTop + helperHeight, windowHeight)) {
      verticalAlignRef.current = "bottom";
    } else {
      verticalAlignRef.current = "top";
    }
    if (isOutsideX(targetLeft + helperWidth, windowWidth)) {
      horizontalAlignRef.current = "left";
    } else {
      horizontalAlignRef.current = "right";
    }
    const coords = {
      top: [x, targetTop - helperHeight - py * 2],
      right: [targetRight + px * 2, y],
      bottom: [x, targetBottom + py * 2],
      left: [targetLeft - helperWidth - px * 2, y],
      center: [
        windowWidth / 2 - helperWidth / 2,
        windowHeight / 2 - helperHeight / 2
      ]
    };
    if (helperPosition === "center" || couldPositionAt(helperPosition)) {
      positionRef.current = helperPosition;
      return coords[helperPosition];
    }
    return autoPosition(coords);
  };
  const p = pos(position);
  return /* @__PURE__ */ React.createElement("div", {
    className: "reactour__popover",
    style: {
      ...getStyles("popover", {
        position: positionRef.current,
        verticalAlign: verticalAlignRef.current,
        horizontalAlign: horizontalAlignRef.current
      }),
      transform: `translate(${Math.round(p[0])}px, ${Math.round(p[1])}px)`
    },
    ref: helperRef,
    ...props
  }, children);
};
var Popover_default = Popover;

// index.tsx
var popover_default = Popover_default;
export {
  Popover_default as Popover,
  popover_default as default
};
