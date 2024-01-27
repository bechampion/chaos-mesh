"use strict";
var __create = Object.create;
var __defProp = Object.defineProperty;
var __getOwnPropDesc = Object.getOwnPropertyDescriptor;
var __getOwnPropNames = Object.getOwnPropertyNames;
var __getProtoOf = Object.getPrototypeOf;
var __hasOwnProp = Object.prototype.hasOwnProperty;
var __export = (target, all) => {
  for (var name in all)
    __defProp(target, name, { get: all[name], enumerable: true });
};
var __copyProps = (to, from, except, desc) => {
  if (from && typeof from === "object" || typeof from === "function") {
    for (let key of __getOwnPropNames(from))
      if (!__hasOwnProp.call(to, key) && key !== except)
        __defProp(to, key, { get: () => from[key], enumerable: !(desc = __getOwnPropDesc(from, key)) || desc.enumerable });
  }
  return to;
};
var __toESM = (mod, isNodeMode, target) => (target = mod != null ? __create(__getProtoOf(mod)) : {}, __copyProps(
  isNodeMode || !mod || !mod.__esModule ? __defProp(target, "default", { value: mod, enumerable: true }) : target,
  mod
));
var __toCommonJS = (mod) => __copyProps(__defProp({}, "__esModule", { value: true }), mod);

// index.tsx
var popover_exports = {};
__export(popover_exports, {
  Popover: () => Popover_default,
  default: () => popover_default
});
module.exports = __toCommonJS(popover_exports);

// Popover.tsx
var import_react = __toESM(require("react"));
var import_utils = require("@reactour/utils");

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
  const helperRef = (0, import_react.useRef)(null);
  const positionRef = (0, import_react.useRef)("");
  const verticalAlignRef = (0, import_react.useRef)("");
  const horizontalAlignRef = (0, import_react.useRef)("");
  const { w: windowWidth, h: windowHeight } = (0, import_utils.getWindow)();
  const getStyles = stylesMatcher(styles);
  const helperRect = (0, import_utils.useRect)(helperRef, refresher);
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
  const [px, py] = (0, import_utils.getPadding)(padding);
  const couldPositionAt = (position2) => {
    return available[position2] > ((0, import_utils.isHoriz)(position2) ? helperWidth + px * 2 : helperHeight + py * 2);
  };
  const autoPosition = (coords) => {
    const positionsOrder = (0, import_utils.bestPositionOf)(available);
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
      const isOutX = (0, import_utils.isOutsideX)(helperPosition[0], windowWidth);
      const isOutY = (0, import_utils.isOutsideY)(helperPosition[1], windowHeight);
      positionRef.current = "custom";
      return [
        isOutX ? windowWidth / 2 - helperWidth / 2 : helperPosition[0],
        isOutY ? windowHeight / 2 - helperHeight / 2 : helperPosition[1]
      ];
    }
    const hX = (0, import_utils.isOutsideX)(targetLeft + helperWidth, windowWidth) ? targetRight - helperWidth + px : targetLeft - px;
    const x = hX > px ? hX : px;
    const hY = (0, import_utils.isOutsideY)(targetTop + helperHeight, windowHeight) ? targetBottom - helperHeight + py : targetTop - py;
    const y = hY > py ? hY : py;
    if ((0, import_utils.isOutsideY)(targetTop + helperHeight, windowHeight)) {
      verticalAlignRef.current = "bottom";
    } else {
      verticalAlignRef.current = "top";
    }
    if ((0, import_utils.isOutsideX)(targetLeft + helperWidth, windowWidth)) {
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
  return /* @__PURE__ */ import_react.default.createElement("div", {
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
// Annotate the CommonJS export names for ESM import in node:
0 && (module.exports = {
  Popover
});
