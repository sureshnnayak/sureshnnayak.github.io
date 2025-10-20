# ShelfHelp: Empowering Visually Impaired with AI-Assisted Shopping

*Published: October 29, 2022 | AAMAS 2023*

## Abstract

The ability to shop independently, especially in grocery stores, is important for maintaining a high quality of life. This can be particularly challenging for people with visual impairments (PVI). Stores carry thousands of products, with approximately 30,000 new products introduced each year in the US market alone, presenting a challenge even for modern computer vision solutions.

Through this work, we present a proof-of-concept socially assistive robotic system we call ShelfHelp, and propose novel technical solutions for enhancing instrumented canes traditionally meant for navigation tasks with additional capability within the domain of shopping.

## Introduction

Shopping for groceries is a fundamental daily activity that most people take for granted. However, for people with visual impairments, this seemingly simple task becomes a significant challenge. Traditional assistive technologies like white canes are primarily designed for navigation and obstacle avoidance, but they don't provide assistance with the complex task of product identification and retrieval in grocery stores.

## Technical Approach

### Visual Product Locator Algorithm

ShelfHelp includes a novel visual product locator algorithm designed specifically for use in grocery stores. The algorithm leverages deep learning techniques to:

- Detect and identify products on store shelves
- Handle the challenge of thousands of different products
- Adapt to new products introduced to the market
- Work effectively in typical grocery store lighting conditions

### MDP-Based Guidance System

The system employs a Markov Decision Process (MDP) framework to generate appropriate verbal manipulation guidance commands. This approach allows the system to:

- Analyze the user's current location and orientation
- Determine the optimal path to the desired product
- Generate clear, actionable verbal instructions
- Adapt guidance based on the user's progress

### System Architecture

The ShelfHelp system consists of several key components:

1. **Computer Vision Module**: Processes camera input to identify products
2. **Navigation System**: Tracks user location and orientation
3. **Guidance Engine**: Generates verbal instructions using MDP
4. **User Interface**: Provides audio feedback to the user

## Experimental Results

Through a comprehensive human subjects study, we demonstrated the system's success in:

- **Product Location**: Successfully locating desired products in grocery store environments
- **Guidance Effectiveness**: Providing effective manipulation guidance for product retrieval
- **User Performance**: Achieving comparable performance to human assistance baseline

### Key Findings

- The system achieved high success rates in product identification
- Users found the verbal guidance clear and actionable
- The system was rated highly on competence, intelligence, and ease of use metrics
- Both autonomous guidance modes performed comparably to human assistance

## Impact and Future Work

This research represents a significant step forward in assistive robotics for people with visual impairments. The ShelfHelp system demonstrates how traditional assistive devices can be enhanced with modern AI capabilities to address complex daily tasks.

### Future Directions

- **Scalability**: Expanding the system to handle more product categories
- **Personalization**: Adapting the system to individual user preferences
- **Integration**: Connecting with store inventory systems for real-time product availability
- **Multi-modal Feedback**: Incorporating haptic feedback alongside verbal guidance

## Conclusion

ShelfHelp represents a novel approach to assistive technology that bridges the gap between navigation assistance and complex task completion. By combining computer vision, machine learning, and human-centered design, we've created a system that empowers people with visual impairments to shop independently.

The positive results from our human subjects study validate the effectiveness of our approach and demonstrate the potential for AI-enhanced assistive technologies to significantly improve quality of life for people with visual impairments.

## References

- Nayak, S., et al. "ShelfHelp: Empowering Humans to Perform Vision-Independent Manipulation Tasks with a Socially Assistive Robotic Cane." *Proceedings of the 22nd International Conference on Autonomous Agents and Multiagent Systems (AAMAS 2023)*, 2023.

## Contact

For questions about this research or the ShelfHelp system, please contact me at [suresh.nayak@email.com](mailto:suresh.nayak@email.com).
