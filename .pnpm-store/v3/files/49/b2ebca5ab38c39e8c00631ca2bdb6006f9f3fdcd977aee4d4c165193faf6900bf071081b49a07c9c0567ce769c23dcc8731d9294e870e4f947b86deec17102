import * as _orval_core from '@orval/core';
import { GenerateMockImports, GeneratorVerbOptions, GeneratorOptions } from '@orval/core';

declare const generateMSWImports: GenerateMockImports;
declare const generateMSW: ({ operationId, response, verb, tags }: GeneratorVerbOptions, { pathRoute, override, context }: GeneratorOptions) => {
    implementation: {
        function: string;
        handler: string;
    };
    imports: _orval_core.GeneratorImport[];
};

export { generateMSW, generateMSWImports };
