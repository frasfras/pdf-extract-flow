#realty 
```mermaid

flowchart TD
    A[realty/] --> B[README.md]
    A --> C[eslint.config.js]
    A --> D[package.json]
    A --> E[tsconfig.json]
    A --> F[.env.template]
    A --> G[.npmrc]
    A --> H[backend/]
    A --> I[frontend/]
    A --> J[scripts/]
    A --> K[shared-models/]
    
    H --> H1[index.ts]
    H --> H2[package.json]
    H --> H3[tsconfig.json]
    H --> H4[database/]
    H --> H5[routes/]
    H --> H6[scripts/]
    H --> H7[services/]
    
    H4 --> H4A[database.ts]
    H4 --> H4B[schema.ts]
    
    H5 --> H5A[asset.ts]
    H5 --> H5B[auth.ts]
    H5 --> H5C[autofill.ts]
    H5 --> H5D[brand-template.ts]
    H5 --> H5E[broker.ts]
    H5 --> H5F[design.ts]
    H5 --> H5G[export.ts]
    H5 --> H5H[flyer.ts]
    H5 --> H5I[property.ts]
    H5 --> H5J[return-nav.ts]
    H5 --> H5K[user.ts]
    
    H6 --> H6A[properties.ts]
    
    H7 --> H7A[broker.ts]
    H7 --> H7B[properties.ts]
    
    I --> I1[declarations.d.ts]
    I --> I2[package.json]
    I --> I3[tsconfig.json]
    I --> I4[webpack.config.ts]
    I --> I5[public/]
    I --> I6[src/]
    
    I5 --> I5A[index.html]
    
    I6 --> I6A[app.tsx]
    I6 --> I6B[config.ts]
    I6 --> I6C[index.tsx]
    I6 --> I6D[theme.ts]
    I6 --> I6E[components/]
    I6 --> I6F[context/]
    I6 --> I6G[hooks/]
    I6 --> I6H[pages/]
    I6 --> I6I[routes/]
    I6 --> I6J[services/]
    
    I6E --> I6E1[alerts.tsx]
    I6E --> I6E2[canva-icon.tsx]
    I6E --> I6E3[demo-alert.tsx]
    I6E --> I6E4[demo-button.tsx]
    I6E --> I6E5[developer-note.tsx]
    I6E --> I6E6[generic-card.tsx]
    I6E --> I6E7[image-carousel.tsx]
    I6E --> I6E8[index.ts]
    I6E --> I6E9[sidebar.tsx]
    I6E --> I6E10[brand-templates/]
    I6E --> I6E11[configure-design/]
    I6E --> I6E12[home/]
    I6E --> I6E13[properties/]
    
    I6E10 --> I6E10A[brand-template-card.tsx]
    
    I6E11 --> I6E11A[configure-design-modal.tsx]
    I6E11 --> I6E11B[index.ts]
    I6E11 --> I6E11C[loading-content.tsx]
    I6E11 --> I6E11D[select-with-preview.tsx]
    I6E11 --> I6E11E[step.tsx]
    
    I6E12 --> I6E12A[connect-button.tsx]
    I6E12 --> I6E12B[index.ts]
    
    I6E13 --> I6E13A[create-design-button.tsx]
    I6E13 --> I6E13B[index.ts]
    I6E13 --> I6E13C[opening-design-modal.tsx]
    I6E13 --> I6E13D[page-header.tsx]
    I6E13 --> I6E13E[property-card.tsx]
    I6E13 --> I6E13F[property-filters.tsx]
    
    I6F --> I6F1[app-context.tsx]
    I6F --> I6F2[index.ts]
    
    I6G --> I6G1[use-configure-design.ts]
    I6G --> I6G2[use-open-in-canva.ts]
    
    I6H --> I6H1[brand-templates.tsx]
    I6H --> I6H2[configure-design.tsx]
    I6H --> I6H3[designs.tsx]
    I6H --> I6H4[error-boundary.tsx]
    I6H --> I6H5[index.ts]
    I6H --> I6H6[properties.tsx]
    I6H --> I6H7[return-nav.tsx]
    
    I6I --> I6I1[index.ts]
    I6I --> I6I2[routes.tsx]
    
    I6J --> I6J1[api.ts]
    I6J --> I6J2[asset.ts]
    I6J --> I6J3[auth.ts]
    I6J --> I6J4[autofill.ts]
    I6J --> I6J5[canva-return.ts]
    I6J --> I6J6[export.ts]
    I6J --> I6J7[field-mapping-validation.ts]
    I6J --> I6J8[flyer.ts]
    I6J --> I6J9[index.ts]
    I6J --> I6J10[property.ts]
    
    J --> J1[start.ts]
    
    K --> K1[package.json]
    K --> K2[tsconfig.json]
    K --> K3[src/]
    
    K3 --> K3A[broker.ts]
    K3 --> K3B[exports.ts]
    K3 --> K3C[flyer.ts]
    K3 --> K3D[index.ts]
    K3 --> K3E[property.ts]
    
    classDef rootNode fill:#ff6b6b,stroke:#333,stroke-width:3px,color:#fff
    classDef folderNode fill:#4ecdc4,stroke:#333,stroke-width:2px,color:#333
    classDef fileNode fill:#ffe66d,stroke:#333,stroke-width:1px,color:#333
    
    class A rootNode
    class H,I,J,K,H4,H5,H6,H7,I5,I6,I6E,I6F,I6G,I6H,I6I,I6J,I6E10,I6E11,I6E12,I6E13,K3 folderNode
    class B,C,D,E,F,G,H1,H2,H3,H4A,H4B,H5A,H5B,H5C,H5D,H5E,H5F,H5G,H5H,H5I,H5J,H5K,H6A,H7A,H7B,I1,I2,I3,I4,I5A,I6A,I6B,I6C,I6D,I6E1,I6E2,I6E3,I6E4,I6E5,I6E6,I6E7,I6E8,I6E9,I6E10A,I6E11A,I6E11B,I6E11C,I6E11D,I6E11E,I6E12A,I6E12B,I6E13A,I6E13B,I6E13C,I6E13D,I6E13E,I6E13F,I6F1,I6F2,I6G1,I6G2,I6H1,I6H2,I6H3,I6H4,I6H5,I6H6,I6H7,I6I1,I6I2,I6J1,I6J2,I6J3,I6J4,I6J5,I6J6,I6J7,I6J8,I6J9,I6J10,J1,K1,K2,K3A,K3B,K3C,K3D,K3E fileNode
