# Creating Excalidraw-Style Diagrams Programmatically

Learn how to generate and manage Excalidraw diagrams through code for better documentation workflows and automated diagram creation.

## Introduction

Excalidraw is an excellent tool for creating hand-drawn style diagrams, but sometimes you need to generate diagrams programmatically. Whether you're building documentation systems, creating automated reports, or integrating diagrams into your applications, this guide will show you how to work with Excalidraw's data format and API.

## Understanding Excalidraw's Data Format

Excalidraw stores diagrams as JSON objects with specific structures. Let's examine the key components:

```javascript
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://excalidraw.com",
  "elements": [
    {
      "id": "element-id",
      "type": "rectangle",
      "x": 100,
      "y": 100,
      "width": 200,
      "height": 100,
      "angle": 0,
      "strokeColor": "#000000",
      "backgroundColor": "#ffffff",
      "fillStyle": "hachure",
      "strokeWidth": 1,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "groupIds": [],
      "frameId": null,
      "roundness": null,
      "seed": 1234567890,
      "versionNonce": 1234567890,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1234567890,
      "link": null,
      "locked": false
    }
  ],
  "appState": {
    "gridSize": null,
    "viewBackgroundColor": "#ffffff"
  },
  "files": {}
}
```

## Setting Up the Development Environment

First, let's set up our development environment:

```bash
# Create project directory
mkdir excalidraw-generator
cd excalidraw-generator

# Initialize Node.js project
npm init -y

# Install dependencies
npm install excalidraw-utils
npm install --save-dev @types/node typescript ts-node

# Install TypeScript
npm install -g typescript
```

## Basic Diagram Generation

Let's start by creating a simple utility to generate basic shapes:

```typescript
interface ExcalidrawElement {
  id: string;
  type: string;
  x: number;
  y: number;
  width: number;
  height: number;
  angle: number;
  strokeColor: string;
  backgroundColor: string;
  fillStyle: string;
  strokeWidth: number;
  strokeStyle: string;
  roughness: number;
  opacity: number;
  groupIds: string[];
  frameId: string | null;
  roundness: any;
  seed: number;
  versionNonce: number;
  isDeleted: boolean;
  boundElements: any;
  updated: number;
  link: string | null;
  locked: boolean;
}

class ExcalidrawGenerator {
  private elements: ExcalidrawElement[] = [];
  private nextId = 1;

  private generateId(): string {
    return `element-${this.nextId++}`;
  }

  private generateSeed(): number {
    return Math.floor(Math.random() * 1000000000);
  }

  private generateVersionNonce(): number {
    return Math.floor(Math.random() * 1000000000);
  }

  addRectangle(x: number, y: number, width: number, height: number, options: Partial<ExcalidrawElement> = {}): ExcalidrawElement {
    const element: ExcalidrawElement = {
      id: this.generateId(),
      type: "rectangle",
      x,
      y,
      width,
      height,
      angle: 0,
      strokeColor: "#000000",
      backgroundColor: "#ffffff",
      fillStyle: "hachure",
      strokeWidth: 1,
      strokeStyle: "solid",
      roughness: 1,
      opacity: 100,
      groupIds: [],
      frameId: null,
      roundness: null,
      seed: this.generateSeed(),
      versionNonce: this.generateVersionNonce(),
      isDeleted: false,
      boundElements: null,
      updated: Date.now(),
      link: null,
      locked: false,
      ...options
    };

    this.elements.push(element);
    return element;
  }

  addText(x: number, y: number, text: string, options: Partial<ExcalidrawElement> = {}): ExcalidrawElement {
    const element: ExcalidrawElement = {
      id: this.generateId(),
      type: "text",
      x,
      y,
      width: text.length * 10, // Approximate width
      height: 20, // Approximate height
      angle: 0,
      strokeColor: "#000000",
      backgroundColor: "transparent",
      fillStyle: "hachure",
      strokeWidth: 1,
      strokeStyle: "solid",
      roughness: 1,
      opacity: 100,
      groupIds: [],
      frameId: null,
      roundness: null,
      seed: this.generateSeed(),
      versionNonce: this.generateVersionNonce(),
      isDeleted: false,
      boundElements: null,
      updated: Date.now(),
      link: null,
      locked: false,
      text: text,
      fontSize: 16,
      fontFamily: 1,
      textAlign: "left",
      verticalAlign: "top",
      ...options
    };

    this.elements.push(element);
    return element;
  }

  addArrow(startX: number, startY: number, endX: number, endY: number, options: Partial<ExcalidrawElement> = {}): ExcalidrawElement {
    const element: ExcalidrawElement = {
      id: this.generateId(),
      type: "arrow",
      x: startX,
      y: startY,
      width: endX - startX,
      height: endY - startY,
      angle: 0,
      strokeColor: "#000000",
      backgroundColor: "transparent",
      fillStyle: "hachure",
      strokeWidth: 2,
      strokeStyle: "solid",
      roughness: 1,
      opacity: 100,
      groupIds: [],
      frameId: null,
      roundness: null,
      seed: this.generateSeed(),
      versionNonce: this.generateVersionNonce(),
      isDeleted: false,
      boundElements: null,
      updated: Date.now(),
      link: null,
      locked: false,
      points: [[0, 0], [endX - startX, endY - startY]],
      lastCommittedPoint: null,
      startBinding: null,
      endBinding: null,
      startArrowhead: null,
      endArrowhead: "arrow",
      ...options
    };

    this.elements.push(element);
    return element;
  }

  generateDiagram(): any {
    return {
      type: "excalidraw",
      version: 2,
      source: "https://excalidraw.com",
      elements: this.elements,
      appState: {
        gridSize: null,
        viewBackgroundColor: "#ffffff"
      },
      files: {}
    };
  }

  exportToJSON(): string {
    return JSON.stringify(this.generateDiagram(), null, 2);
  }
}
```

## Creating Common Diagram Types

Let's create some utility functions for common diagram patterns:

```typescript
class DiagramTemplates {
  static createFlowchart(generator: ExcalidrawGenerator): void {
    // Start node
    generator.addRectangle(100, 50, 120, 60, {
      backgroundColor: "#e1f5fe",
      strokeColor: "#0277bd"
    });
    generator.addText(130, 80, "Start", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    // Process node
    generator.addRectangle(100, 150, 120, 60, {
      backgroundColor: "#f3e5f5",
      strokeColor: "#7b1fa2"
    });
    generator.addText(130, 180, "Process", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    // Decision node (diamond shape)
    generator.addRectangle(100, 250, 120, 60, {
      backgroundColor: "#fff3e0",
      strokeColor: "#f57c00",
      roundness: { type: 3 } // Diamond shape
    });
    generator.addText(130, 280, "Decision", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    // End node
    generator.addRectangle(100, 350, 120, 60, {
      backgroundColor: "#ffebee",
      strokeColor: "#c62828"
    });
    generator.addText(130, 380, "End", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    // Arrows
    generator.addArrow(160, 110, 160, 150); // Start to Process
    generator.addArrow(160, 210, 160, 250); // Process to Decision
    generator.addArrow(160, 310, 160, 350); // Decision to End
  }

  static createSystemArchitecture(generator: ExcalidrawGenerator): void {
    // Frontend
    generator.addRectangle(50, 100, 100, 80, {
      backgroundColor: "#e8f5e8",
      strokeColor: "#2e7d32"
    });
    generator.addText(100, 140, "Frontend", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    // API Gateway
    generator.addRectangle(200, 100, 100, 80, {
      backgroundColor: "#fff3e0",
      strokeColor: "#f57c00"
    });
    generator.addText(250, 140, "API Gateway", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    // Backend Services
    generator.addRectangle(350, 50, 100, 80, {
      backgroundColor: "#e3f2fd",
      strokeColor: "#1976d2"
    });
    generator.addText(400, 90, "Service A", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    generator.addRectangle(350, 150, 100, 80, {
      backgroundColor: "#e3f2fd",
      strokeColor: "#1976d2"
    });
    generator.addText(400, 190, "Service B", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    // Database
    generator.addRectangle(500, 100, 100, 80, {
      backgroundColor: "#fce4ec",
      strokeColor: "#c2185b"
    });
    generator.addText(550, 140, "Database", {
      textAlign: "center",
      verticalAlign: "middle"
    });

    // Connections
    generator.addArrow(150, 140, 200, 140); // Frontend to API
    generator.addArrow(300, 140, 350, 90);  // API to Service A
    generator.addArrow(300, 140, 350, 190); // API to Service B
    generator.addArrow(450, 90, 500, 140);  // Service A to DB
    generator.addArrow(450, 190, 500, 140); // Service B to DB
  }

  static createUserJourney(generator: ExcalidrawGenerator): void {
    const steps = [
      { x: 50, y: 200, text: "Landing Page" },
      { x: 200, y: 200, text: "Sign Up" },
      { x: 350, y: 200, text: "Onboarding" },
      { x: 500, y: 200, text: "Dashboard" },
      { x: 650, y: 200, text: "Feature Use" }
    ];

    steps.forEach((step, index) => {
      generator.addRectangle(step.x, step.y, 100, 60, {
        backgroundColor: index === 0 ? "#e8f5e8" : "#f5f5f5",
        strokeColor: index === 0 ? "#2e7d32" : "#666666"
      });
      generator.addText(step.x + 50, step.y + 30, step.text, {
        textAlign: "center",
        verticalAlign: "middle"
      });

      if (index < steps.length - 1) {
        generator.addArrow(step.x + 100, step.y + 30, steps[index + 1].x, steps[index + 1].y + 30);
      }
    });
  }
}
```

## Integration with Web Applications

Here's how to integrate Excalidraw generation into a web application:

```typescript
// Express.js server example
import express from 'express';
import { ExcalidrawGenerator, DiagramTemplates } from './excalidraw-generator';

const app = express();
app.use(express.json());

app.post('/api/generate-diagram', (req, res) => {
  const { type, options } = req.body;
  
  const generator = new ExcalidrawGenerator();
  
  switch (type) {
    case 'flowchart':
      DiagramTemplates.createFlowchart(generator);
      break;
    case 'architecture':
      DiagramTemplates.createSystemArchitecture(generator);
      break;
    case 'user-journey':
      DiagramTemplates.createUserJourney(generator);
      break;
    default:
      return res.status(400).json({ error: 'Unknown diagram type' });
  }
  
  const diagram = generator.generateDiagram();
  res.json(diagram);
});

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

## Advanced Features

### Custom Shape Generation

```typescript
class CustomShapes {
  static createDatabaseShape(generator: ExcalidrawGenerator, x: number, y: number, width: number, height: number): void {
    // Main rectangle
    generator.addRectangle(x, y, width, height, {
      backgroundColor: "#fce4ec",
      strokeColor: "#c2185b"
    });
    
    // Cylinder top
    generator.addEllipse(x, y - 10, width, 20, {
      backgroundColor: "#fce4ec",
      strokeColor: "#c2185b"
    });
    
    // Cylinder bottom
    generator.addEllipse(x, y + height - 10, width, 20, {
      backgroundColor: "#fce4ec",
      strokeColor: "#c2185b"
    });
  }

  static createCloudShape(generator: ExcalidrawGenerator, x: number, y: number, width: number, height: number): void {
    // Create a cloud using multiple ellipses
    const ellipses = [
      { x: x + width * 0.2, y: y + height * 0.3, w: width * 0.3, h: height * 0.4 },
      { x: x + width * 0.4, y: y, w: width * 0.4, h: height * 0.6 },
      { x: x + width * 0.6, y: y + height * 0.2, w: width * 0.3, h: height * 0.5 },
      { x: x + width * 0.1, y: y + height * 0.5, w: width * 0.4, h: height * 0.3 },
      { x: x + width * 0.5, y: y + height * 0.6, w: width * 0.4, h: height * 0.3 }
    ];

    ellipses.forEach(ellipse => {
      generator.addEllipse(ellipse.x, ellipse.y, ellipse.w, ellipse.h, {
        backgroundColor: "#e3f2fd",
        strokeColor: "#1976d2",
        fillStyle: "solid"
      });
    });
  }
}
```

### Animation and Interactivity

```typescript
class AnimatedDiagram {
  static createAnimatedFlow(generator: ExcalidrawGenerator): void {
    const nodes = [
      { x: 100, y: 100, text: "Step 1" },
      { x: 300, y: 100, text: "Step 2" },
      { x: 500, y: 100, text: "Step 3" }
    ];

    nodes.forEach((node, index) => {
      generator.addRectangle(node.x, node.y, 100, 60, {
        backgroundColor: "#e8f5e8",
        strokeColor: "#2e7d32",
        customData: {
          animationDelay: index * 1000, // 1 second delay between animations
          animationType: "fadeIn"
        }
      });
      generator.addText(node.x + 50, node.y + 30, node.text, {
        textAlign: "center",
        verticalAlign: "middle"
      });
    });
  }
}
```

## Best Practices

1. **Consistent Styling**: Use a color palette and consistent styling across your diagrams
2. **Responsive Design**: Consider how diagrams will look at different sizes
3. **Accessibility**: Ensure diagrams are accessible with proper contrast and text alternatives
4. **Performance**: For large diagrams, consider lazy loading and optimization techniques

## Conclusion

Programmatic diagram generation with Excalidraw opens up many possibilities for automated documentation, reporting, and visualization. By understanding the data format and building utility functions, you can create sophisticated diagram generation systems that integrate seamlessly with your applications.

### Key Takeaways

- Excalidraw uses a well-defined JSON format for diagrams
- You can generate diagrams programmatically using TypeScript/JavaScript
- Common patterns can be abstracted into reusable templates
- Integration with web applications is straightforward
- Consider performance and accessibility in your implementations

### Next Steps

- Explore Excalidraw's plugin system for advanced features
- Implement real-time collaboration features
- Add support for custom shapes and elements
- Integrate with your existing documentation workflow

---

*This article is part of my series on developer tools and automation. Check out my other articles for more insights into building efficient development workflows!*
