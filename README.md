# Learning-docs
Contains All Latest Docs
### How to create the Dynamic Loading :-
```
import React, { useState, useEffect } from 'react';

const DynamicImportExample = () => {
  const [dynamicComponents, setDynamicComponents] = useState([]);

  useEffect(() => {
    const loadDynamicComponents = async () => {
      const componentNames = ['ComponentA', 'ComponentB', 'ComponentC'];

      const components = await Promise.all(
        componentNames.map(async (componentName) => {
          // Dynamically import the component using import()
          const dynamicComponent = await import(`./${componentName}`);
          return { name: componentName, component: dynamicComponent.default };
        })
      );

      setDynamicComponents(components);
    };

    loadDynamicComponents();
  }, []); // Ensure the effect runs only once

  return (
    <div>
      <h1>Dynamic Import Example</h1>
      {dynamicComponents.map(({ name, component: DynamicComponent }) => (
        <div key={name}>
          <h2>{name}</h2>
          <DynamicComponent />
        </div>
      ))}
    </div>
  );
};

export default DynamicImportExample;








```
