import React$1 from 'react';
import { RectResult } from '@reactour/utils';

declare type StylesKeys = 'popover';
declare type StylesObj = {
    [key in StylesKeys]?: StyleFn;
};
declare type StyleFn = (props: {
    [key: string]: any;
}, state?: {
    [key: string]: any;
}) => React.CSSProperties;

declare const Popover: React$1.FC<PopoverProps>;

declare type PopoverProps = {
    sizes: RectResult;
    children?: React$1.ReactNode;
    position?: PositionType;
    padding?: number | [number, number];
    styles?: StylesObj;
    className?: string;
    refresher?: any;
};
declare type PositionType = Position | ((postionsProps: PositionProps, prevRect: RectResult) => Position);
declare type PositionProps = RectResult & {
    windowWidth: number;
    windowHeight: number;
};
declare type Position = 'top' | 'right' | 'bottom' | 'left' | 'center' | [number, number];

export { Popover, StylesObj as PopoverStylesObj, PositionType as Position, PositionProps, Popover as default };
