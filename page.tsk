"use client"

import { useState } from "react"
import { ShoppingCart, Calculator } from "lucide-react"
import { Button } from "@/components/ui/button"
import { Input } from "@/components/ui/input"
import { useToast } from "@/hooks/use-toast"
import Link from "next/link"

interface MenuItem {
  id: string
  title: string
  price: number
  description: string
  category: string
  subcategory: string
  minimum?: number
  serves?: number | string
  cuisine?: string[]
  mealType?: string[]
}

const menuData: MenuItem[] = [
  // Breakfast Platters
  {
    id: "bp1",
    title: "Assorted Bagels Breakfast Platter",
    price: 5.95,
    description: "Full size bagels and bialys served with butter, fruit jam and assorted cream cheeses.",
    category: "Breakfast",
    subcategory: "Breakfast Platters",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast"],
  },
  {
    id: "bp2",
    title: "Mini-Size Breakfast Platter",
    price: 8.95,
    description:
      "An assortment of mini bagels, homemade mini muffins, danishes, croissants, scones and homemade breakfast bread served with fruit jam, butter and assorted cream cheeses.",
    category: "Breakfast",
    subcategory: "Breakfast Platters",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast"],
  },
  {
    id: "bp3",
    title: "Smoked Salmon Breakfast Platter",
    price: 19.95,
    description:
      "Smoked salmon, hard boiled eggs, red onion, caper berries, sliced tomatoes, lemon wedges and sliced cucumbers with a tray of assorted miniature bagels, flavored cream cheeses and sweet butter.",
    category: "Breakfast",
    subcategory: "Breakfast Platters",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Seafood"],
    mealType: ["Breakfast", "Brunch"],
  },
  {
    id: "bp4",
    title: "Savory Miniature Sandwiches and Pinwheels Breakfast Platter",
    price: 13.95,
    description: "2 per guest.",
    category: "Breakfast",
    subcategory: "Breakfast Platters",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast"],
  },
  {
    id: "bp5",
    title: "Healthy Breakfast Platter",
    price: 10.95,
    description:
      "Multigrain, energy and whole wheat bagels, low fat yogurt loaves, low fat and fat free muffins, multigrain breads with fruit preserves, low-fat butter or margarine and low-fat and vegetable cream cheeses.",
    category: "Breakfast",
    subcategory: "Breakfast Platters",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Healthy"],
    mealType: ["Breakfast"],
  },

  // Hot Breakfast
  {
    id: "hb1",
    title: "Hot Oatmeal Breakfast Tray",
    price: 8.5,
    description: "Accompanied by granola, chopped fruits, berries, brown sugar, cinnamon, raisins, nuts and honey.",
    category: "Breakfast",
    subcategory: "Hot Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Healthy"],
    mealType: ["Breakfast"],
  },
  {
    id: "hb2",
    title: "Hot Cream of Wheat Breakfast Tray",
    price: 8.5,
    description: "Accompanied by granola, chopped fruits, berries, brown sugar, cinnamon, raisins, nuts and honey.",
    category: "Breakfast",
    subcategory: "Hot Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Healthy"],
    mealType: ["Breakfast"],
  },
  {
    id: "hb3",
    title: "Breakfast Burritos, Panini, Croissant and English Muffins Breakfast Tray",
    price: 10.95,
    description:
      "Chef's selection of eggs and egg whites with variety of breakfast meats and cheeses served warm in a chafing dish.",
    category: "Breakfast",
    subcategory: "Hot Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Mexican"],
    mealType: ["Breakfast"],
  },
  {
    id: "hb4",
    title: "Omelette Buffet Breakfast Tray",
    price: 25.95,
    description:
      "Assorted varieties of omelettes served on chafing dishes and accompanied by assorted bread, country style potatoes, bacon, turkey bacon, sausage patties, sliced fresh fruit, coffee service and fresh orange juice.",
    category: "Breakfast",
    subcategory: "Hot Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast", "Brunch"],
  },
  {
    id: "hb5",
    title: "Berry Pancake Trio and Crusted French Toast Breakfast Tray",
    price: 11.95,
    description:
      "Stack of buttermilk, strawberry and banana pancakes and Grand Marnier cinnamon French toast. Served with pure maple syrup and sweet butter served warm in a chafing dish.",
    category: "Breakfast",
    subcategory: "Hot Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast"],
  },
  {
    id: "hb6",
    title: "The Belgian Waffle Breakfast Tray",
    price: 9.95,
    description:
      "Freshly made plain or fruit filled waffles accompanied by warm maple syrup, breakfast butter, whipped cream and fresh seasonal fruit sauce.",
    category: "Breakfast",
    subcategory: "Hot Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Belgian"],
    mealType: ["Breakfast"],
  },
  {
    id: "hb7",
    title: "Omelettes Bar Breakfast Tray",
    price: 26.95,
    description:
      "Made to order omelettes. Includes: egg whites, whole eggs, 3 meat selections, 6 veggie selections, bagel and bread platter, fresh fruit and berries, coffee service and freshly squeezed orange juice.",
    category: "Breakfast",
    subcategory: "Hot Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast", "Brunch"],
  },

  // Light and Healthy Breakfast
  {
    id: "lh1",
    title: "Fruit Salad Breakfast Tray",
    price: 8.5,
    description:
      "Selection of seasonal fruits, including: pineapple, honeydew, cantaloupe, papaya, berries and other exotic fruits of the season.",
    category: "Breakfast",
    subcategory: "Light & Healthy Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["Healthy", "Fruit"],
    mealType: ["Breakfast", "Snack"],
  },
  {
    id: "lh2",
    title: "Fruit Skewers Breakfast Tray",
    price: 9.5,
    description: "Selection of cut-up seasonal fruits fixed on skewers.",
    category: "Breakfast",
    subcategory: "Light & Healthy Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["Healthy", "Fruit"],
    mealType: ["Breakfast", "Snack"],
  },
  {
    id: "lh3",
    title: "Sliced Fruits Breakfast Tray",
    price: 8.5,
    description:
      "Arranged and garnished selection of fresh seasonal fruits, including: pineapple, honeydew, cantaloupe, papaya, mixed berries and other succulent fruits.",
    category: "Breakfast",
    subcategory: "Light & Healthy Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["Healthy", "Fruit"],
    mealType: ["Breakfast", "Snack"],
  },
  {
    id: "lh4",
    title: "Whole Fruits Breakfast Tray",
    price: 4.95,
    description:
      "Red delicious and granny smith apples, Valencia oranges, baby bananas, seedless grapes and other seasonal fruits.",
    category: "Breakfast",
    subcategory: "Light & Healthy Breakfast",
    minimum: 6,
    cuisine: ["Healthy", "Fruit"],
    mealType: ["Breakfast", "Snack"],
  },
  {
    id: "lh5",
    title: "Mixed Berries Breakfast Tray",
    price: 9.95,
    description: "Fresh seasonal berries in a bowl.",
    category: "Breakfast",
    subcategory: "Light & Healthy Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["Healthy", "Fruit"],
    mealType: ["Breakfast", "Snack"],
  },
  {
    id: "lh6",
    title: "Homemade Individual Yogurt Parfait Breakfast Tray",
    price: 7.95,
    description:
      "Individual cups of homemade low-fat berry yogurt or vanilla yogurt layered with seasonal berries, bananas and homemade nut and raisin granola.",
    category: "Breakfast",
    subcategory: "Light & Healthy Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["Healthy", "American"],
    mealType: ["Breakfast", "Snack"],
  },
  {
    id: "lh7",
    title: "Yogurt Bar Breakfast Tray",
    price: 11.95,
    description:
      "California breakfast parfait, bowl of organic low-fat plain, strawberry and vanilla yogurt, homemade granola and sliced bananas, chopped fruits and seasonal berries.",
    category: "Breakfast",
    subcategory: "Light & Healthy Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["Healthy", "American"],
    mealType: ["Breakfast"],
  },
  {
    id: "lh8",
    title: "Greek Yogurt Bar Breakfast Tray",
    price: 8.95,
    description:
      "Greek low-fat plain, strawberry and vanilla yogurt, homemade granola and sliced bananas, chopped fruits and seasonal berries.",
    category: "Breakfast",
    subcategory: "Light & Healthy Breakfast",
    minimum: 6,
    cuisine: ["Healthy", "American"],
    mealType: ["Breakfast"],
  },

  // Breakfast Packages
  {
    id: "bpkg1",
    title: "Continental Corporate Breakfast Package",
    price: 15.95,
    description:
      "Sliced fresh fruit platter and assorted mini bagels, mini muffins, danishes, croissants and pastries with preserves, sweet butter and cream cheese.",
    category: "Breakfast",
    subcategory: "Breakfast Packages",
    minimum: 8,
    serves: 1,
    cuisine: ["American", "European"],
    mealType: ["Breakfast", "Corporate"],
  },
  {
    id: "bpkg2",
    title: "Continental Executive Breakfast Package",
    price: 17.95,
    description:
      "Assorted mini bagels, mini muffins, danishes, croissants, and pastries with preserves, sweet butter and cream cheese, sliced fresh fruit platter, freshly squeezed orange juice and coffee service.",
    category: "Breakfast",
    subcategory: "Breakfast Packages",
    minimum: 8,
    serves: 1,
    cuisine: ["American", "European"],
    mealType: ["Breakfast", "Corporate"],
  },
  {
    id: "bpkg3",
    title: "Executive Breakfast Package",
    price: 16.95,
    description:
      "English farmhouse cheddar, French Brie, Holland Gouda and Danish Havarti, freshly baked mini muffins, mini croissants, loaf cakes, cranberry raisin nut rolls, sweet butter and preserves.",
    category: "Breakfast",
    subcategory: "Breakfast Packages",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European"],
    mealType: ["Breakfast"],
  },
  {
    id: "bpkg4",
    title: "Board of Directors Breakfast Package",
    price: 29.95,
    description:
      "Mini bagels, pastries and muffins with butter and preserves, grilled breakfast wraps and paninis, yogurt parfait bar, fresh sliced fruit skewers, fresh squeezed orange, apple and tomato juices, freshly brewed house blend coffee and tea and bottled cold water.",
    category: "Breakfast",
    subcategory: "Breakfast Packages",
    minimum: 10,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast", "Corporate"],
  },
  {
    id: "bpkg5",
    title: "Spa Breakfast Package",
    price: 18.95,
    description:
      "Whole grain muffins, loaf cakes and whole grain bagels served with low-fat and regular cream cheese, butter and preserves. Accompanied by Greek yogurt with honey, granola and fresh fruit and hard boiled eggs.",
    category: "Breakfast",
    subcategory: "Breakfast Packages",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Healthy"],
    mealType: ["Breakfast"],
  },
  {
    id: "bpkg6",
    title: "American Breakfast Package",
    price: 21.95,
    description:
      "Fresh scrambled eggs, fluffy buttermilk pancakes or challah French toast, link sausage, bacon, turkey bacon, home fried potatoes, breakfast pastries, bagels and muffins, cream cheese and fruit preserves, coffee service, assorted chilled juices and sliced fruits.",
    category: "Breakfast",
    subcategory: "Breakfast Packages",
    minimum: 10,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast", "Brunch"],
  },
  {
    id: "bpkg7",
    title: "El Mariachi Breakfast Package",
    price: 21.95,
    description:
      "Fluffy scrambled eggs, thick-sliced bacon, golden breakfast sausage, vegetarian refried beans, warm flour tortillas, taco shells, shredded cheese, pico de gallo, sour cream, guacamole, fresh salsa.",
    category: "Breakfast",
    subcategory: "Breakfast Packages",
    minimum: 10,
    serves: 1,
    cuisine: ["Mexican"],
    mealType: ["Breakfast"],
  },
  {
    id: "bpkg8",
    title: "Brunch Buffet Breakfast Package",
    price: 28.95,
    description:
      "Lox, mini bagels, cream cheese, capers and red onion, eggs Benedict, Belgian waffles with syrup and butter, farmers scrambled eggs, kielbasa sausage, hickory smoked bacon, country-fried potatoes with bell peppers and onions, seasonal fresh fruit, croissants, assorted muffins and breads with butter and jam, apple dumplings with a warm caramel sauce and assorted fruit juices, coffee and tea.",
    category: "Breakfast",
    subcategory: "Breakfast Packages",
    minimum: 10,
    serves: 1,
    cuisine: ["American", "European", "Seafood"],
    mealType: ["Brunch"],
  },

  // Different Breakfast
  {
    id: "db1",
    title: "Frittata Primavera Diamonds Breakfast Tray",
    price: 9.95,
    description: "Baked with whole eggs or egg whites. Your choice of style.",
    category: "Breakfast",
    subcategory: "Different Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian", "Healthy"],
    mealType: ["Breakfast", "Brunch"],
  },
  {
    id: "db2",
    title: "Strata Breakfast Tray",
    price: 15.5,
    description: "Savory bread pudding with eggs and cheese.",
    category: "Breakfast",
    subcategory: "Different Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Breakfast"],
  },
  {
    id: "db3",
    title: "Large Quiche Breakfast Pie",
    price: 25.0,
    description: "Large quiche pie.",
    category: "Breakfast",
    subcategory: "Different Breakfast",
    cuisine: ["French"],
    mealType: ["Breakfast", "Brunch"],
  },
  {
    id: "db4",
    title: "French Crepe Melody Breakfast Tray",
    price: 12.95,
    description: "Cheese blitzes with apple sauce, sour cream and blueberry compote, or savory crepes.",
    category: "Breakfast",
    subcategory: "Different Breakfast",
    minimum: 6,
    serves: 1,
    cuisine: ["French"],
    mealType: ["Breakfast"],
  },

  // Breakfast Beverages
  {
    id: "bbev1",
    title: "Freshly Squeezed Juice Breakfast",
    price: 4.5,
    description: "Fresh squeezed juice.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["Healthy"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev2",
    title: "Fully Coffee and Tea Service Breakfast",
    price: 5.99,
    description: "Complete coffee and tea service.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev3",
    title: "Only Coffee Breakfast",
    price: 3.99,
    description: "Coffee service only.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev4",
    title: "Only Tea Breakfast",
    price: 3.99,
    description: "Tea service only.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev5",
    title: "Hot Chocolate Breakfast",
    price: 4.95,
    description: "Hot Belgian chocolate served with steamed milk and sweeteners.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["Belgian"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev6",
    title: "Hot Apple Cider Breakfast",
    price: 4.95,
    description: "Hot apple cider.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev7",
    title: "Assorted Canned Breakfast Beverages",
    price: 3.0,
    description: "Assorted canned beverages.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev8",
    title: "Spring Water Breakfast",
    price: 2.0,
    description: "Bottled spring water.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    cuisine: ["Healthy"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev9",
    title: "Snapple Breakfast",
    price: 3.99,
    description: "Assorted Snapple flavors.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev10",
    title: "San Pellegrino Breakfast",
    price: 4.0,
    description: "San Pellegrino sparkling water.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev11",
    title: "Perrier Breakfast",
    price: 4.95,
    description: "Perrier sparkling water.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["French"],
    mealType: ["Beverage"],
  },
  {
    id: "bbev12",
    title: "Individual Juice Breakfast",
    price: 4.95,
    description: "Individual juice bottles.",
    category: "Breakfast",
    subcategory: "Breakfast Beverages",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Beverage"],
  },

  // Salad Entrees
  {
    id: "se1",
    title: "California Chicken Salad Tray",
    price: 14.95,
    description:
      "Grilled chicken, avocado, asparagus, alfalfa sprouts, cucumber, carrots, goat cheese, red onion and tomato on a bed of mixed greens. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["American", "Healthy"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se2",
    title: "Mediterranean Rosemary Chicken and Figs Salad Tray",
    price: 14.95,
    description:
      "Comes with olives, mushrooms, red peppers, goat cheese, almonds and apples on a bed of field greens. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["Mediterranean"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se3",
    title: "Grilled Chicken Caesar Salad Tray",
    price: 12.95,
    description:
      "Marinated chicken breast, crisp romaine lettuce, garlic Parmesan croutons, Roma tomatoes and served with Caesar dressing. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["American", "Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se4",
    title: "Pesto Grilled Jumbo Shrimp Salad Tray",
    price: 16.95,
    description:
      "Served over baby greens and toasted hazelnuts, with goat cheese, roasted fennel, grilled asparagus, grilled eggplant and Kalamata olives. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["Italian", "Seafood"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se5",
    title: "Sesame Seared Tuna Salad Tray",
    price: 17.95,
    description:
      "Sashimi grade tuna, shiitake mushrooms and cellophane noodles. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["Asian", "Seafood"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se6",
    title: "Asian Tuna Salad Tray",
    price: 17.95,
    description:
      "Grilled yellowfin tuna with Chinese cabbage, bok choy, carrots, cucumbers, daikon radishes, scallions, sesame seeds and orange soy ginger dressing. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["Asian", "Seafood"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se7",
    title: "Grilled Salmon Nicoise Salad Tray",
    price: 15.95,
    description:
      "Grilled salmon served with lemon zested green beans and shallots, roasted potatoes, plum tomatoes, hard boiled eggs and olives over romaine lettuce. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["French", "Seafood"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se8",
    title: "Grilled Tuna Nicoise Salad Tray",
    price: 17.95,
    description:
      "Grilled tuna served with lemon zested green beans and shallots, roasted potatoes, plum tomatoes, hard boiled eggs and olives over romaine lettuce. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["French", "Seafood"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se9",
    title: "Filet Mignon Salad Tray",
    price: 18.95,
    description:
      "Served on a bed of arugula with roasted peppers, caramelized onions and grilled portobello mushrooms. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["American", "Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se10",
    title: "Santa Fe BBQ Shrimp Salad Tray",
    price: 16.95,
    description:
      "Jumbo imported shrimp tossed with homemade BBQ sauce, sweet corn, black beans, diced tomatoes and lime vinaigrette on a bed of organic field greens. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["Mexican", "American", "Seafood"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "se11",
    title: "Roasted Big Vegetable Salad Tray",
    price: 12.95,
    description:
      "Fresh roasted carrots, mushrooms, Brussels sprouts, asparagus, sweet corn and broccoli mixed with organic baby greens. Served with a basket of sliced baguette.",
    category: "Salads",
    subcategory: "Salad Entrees",
    minimum: 6,
    cuisine: ["Healthy", "Vegetarian"],
    mealType: ["Lunch", "Dinner"],
  },

  // Poultry Entrees - Adding ALL chicken dishes from the menu
  {
    id: "pe1",
    title: "Apricot Ginger Chicken Breast Tray",
    price: 18.95,
    description:
      "Marinated with fresh ginger, apricot preserve, soy sauce, scallions and cilantro. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Asian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "pe2",
    title: "Curried Chicken Tray",
    price: 18.95,
    description:
      "Comes with potatoes, carrots, onions, raisins, toasted coconut and chopped fresh mint. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Indian", "Asian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe3",
    title: "Tamari Glazed Chicken Tray",
    price: 18.95,
    description:
      "Shiitake mushrooms, red peppers and cilantro. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Asian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe4",
    title: "Balsamic Glazed Breast of Chicken Tray",
    price: 18.95,
    description: "Diced Roma tomatoes and basil. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "pe5",
    title: "Citrus Glazed Chicken Tray",
    price: 18.95,
    description:
      "Comes with orange sweet and sour glaze. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Asian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "pe6",
    title: "Apricot Chicken Tray",
    price: 18.95,
    description:
      "Boneless breast sauteed in a light cream sauce with dried apricots and Grand Marnier. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["French", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "pe7",
    title: "Chicken a la Greque Tray",
    price: 18.95,
    description:
      "Grilled chicken, garlic sauce, tomatoes, Kalamata olives, feta, parsley and lemon. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Greek", "Mediterranean"],
    mealType: ["Dinner"],
  },
  {
    id: "pe8",
    title: "Chicken Tikka Masala Tray",
    price: 18.95,
    description:
      "Chicken, tikka masala sauce, green onions, eggplant, red peppers, cilantro and lemon. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Indian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe9",
    title: "Chicken Piccata Tray",
    price: 18.95,
    description:
      "Comes with capers, lemon juice and white wine. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe10",
    title: "Chicken Cacciatore Tray",
    price: 18.95,
    description:
      "Comes with tomato, mushrooms, onion and olives. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe11",
    title: "Chicken Francaise Tray",
    price: 18.95,
    description:
      "Lemon, butter and Chardonnay sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "pe12",
    title: "Chicken Tuscano Tray",
    price: 18.95,
    description:
      "Chunks of chicken sauteed in olive oil, garlic, parsley, white wine sauce, artichoke hearts and sun-dried tomatoes. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe13",
    title: "Chicken Parmigiana Tray",
    price: 18.95,
    description:
      "Comes with fresh tomato basil sauce, mozzarella cheese and shaved Parmesan. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe14",
    title: "Chicken Salina Tray",
    price: 18.95,
    description:
      "Comes with artichokes, sun-dried tomatoes, portobello mushrooms and basil with lemon butter sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe15",
    title: "Chicken Savoyard Tray",
    price: 18.95,
    description:
      "Made in creamy sauce of Gruyere, white wine, Dijon mustard and tarragon. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["French", "Swiss"],
    mealType: ["Dinner"],
  },
  {
    id: "pe16",
    title: "Chicken Milanese Tray",
    price: 18.95,
    description:
      "Parmesan crusted chicken with baby spinach, tomatoes and balsamic sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe17",
    title: "Chicken Marseille Tray",
    price: 18.95,
    description:
      "Sauteed medallion of chicken with artichoke hearts, eggplant and vine ripe tomatoes in a Chardonnay sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["French", "Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe18",
    title: "Stuffed Chicken Roulade with Fresh Mozzarella Tray",
    price: 18.95,
    description:
      "Spinach, roasted pepper and sun-dried tomatoes in a beurre blanc cream sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian", "French"],
    mealType: ["Dinner"],
  },
  {
    id: "pe19",
    title: "Stuffed Chicken Roulade with Spinach Tray",
    price: 18.95,
    description:
      "Boursin cheese and sun-dried tomatoes. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["French"],
    mealType: ["Dinner"],
  },
  {
    id: "pe20",
    title: "Stuffed Chicken Roulade with Portobello Mushrooms Tray",
    price: 18.95,
    description:
      "Sweet peppers with an aged balsamic and fig honey glaze. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "pe21",
    title: "Stuffed Chicken Roulade with Herb Goat Cheese Tray",
    price: 18.95,
    description:
      "Portobello mushrooms, asparagus and red pepper coulis. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "French"],
    mealType: ["Dinner"],
  },
  {
    id: "pe22",
    title: "Chicken Kebab with Tahini Dip Tray",
    price: 18.95,
    description: "Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Middle Eastern"],
    mealType: ["Dinner"],
  },
  {
    id: "pe23",
    title: "Stuffed Poussin Tray",
    price: 18.95,
    description:
      "Comes with risotto and wild mushrooms. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["French", "Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe24",
    title: "Sage Infused Roasted Turkey Tray",
    price: 15.95,
    description:
      "Turkey breast with cranberry orange relish. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["American"],
    mealType: ["Dinner", "Thanksgiving"],
  },
  {
    id: "pe25",
    title: "Sun-Dried Tomato and Parmesan Crusted Chicken Tray",
    price: 15.95,
    description:
      "Artichoke, tomato and roasted pepper relish. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "pe26",
    title: "Mexicali Chicken Tray",
    price: 18.95,
    description:
      "Melted sharp cheddar, pico de gallo, peppers and onions. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Mexican"],
    mealType: ["Dinner"],
  },
  {
    id: "pe27",
    title: "Chicken Marsala Tray",
    price: 15.95,
    description: "Mushroom Marsala sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe28",
    title: "Sesame Crusted Teriyaki Chicken Tray",
    price: 15.95,
    description: "Sauteed bok choy. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["Asian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe29",
    title: "Skinless Crisp Oven Fried Chicken Tray",
    price: 15.95,
    description: "Cornflake and rosemary crust. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["American"],
    mealType: ["Dinner", "Comfort Food"],
  },
  {
    id: "pe30",
    title: "Traditional Southern Fried Chicken Tray",
    price: 15.95,
    description:
      "Marinated in buttermilk, herbs and spices. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["American", "Southern"],
    mealType: ["Dinner", "Comfort Food"],
  },
  {
    id: "pe31",
    title: "Roasted Garlic Lemon Herb Chicken Tray",
    price: 15.95,
    description:
      "Roasted vegetable melange, fresh lemon zest and roasted garlic and herbs. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["Mediterranean", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "pe32",
    title: "Stir-Fried Chicken Tray",
    price: 15.95,
    description:
      "Peppers, onions, green beans and water chestnuts in a garlic oyster sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["Asian"],
    mealType: ["Dinner"],
  },
  {
    id: "pe33",
    title: "Lemon Dijon Chicken Tray",
    price: 15.95,
    description:
      "Roasted artichoke hearts, sun-dried tomatoes and basil and lemon Dijon sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Poultry Entrees",
    minimum: 6,
    cuisine: ["French", "American"],
    mealType: ["Dinner"],
  },

  // Beef Entrees - Adding ALL beef dishes
  {
    id: "be1",
    title: "Leg of Lamb Tray",
    price: 24.95,
    description:
      "Stuffed with pine nuts, mint, parsley and Dijon mustard. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Mediterranean", "European"],
    mealType: ["Dinner", "Special Occasion"],
  },
  {
    id: "be2",
    title: "Lamb Kebab Skewered Tray",
    price: 21.95,
    description:
      "Grilled to perfection. Marinated cubes of New Zealand lamb. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Middle Eastern", "Mediterranean"],
    mealType: ["Dinner"],
  },
  {
    id: "be3",
    title: "Lamb Stew Tray",
    price: 21.95,
    description: "Served with parsnips and figs. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["European", "Comfort Food"],
    mealType: ["Dinner"],
  },
  {
    id: "be4",
    title: "Roasted Lamb Chops Tray",
    price: 27.95,
    description:
      "Served with Dijon and herb crust with tahini sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Mediterranean", "European"],
    mealType: ["Dinner", "Special Occasion"],
  },
  {
    id: "be5",
    title: "Stuffed Filet Mignon with Sauteed Mushrooms Tray",
    price: 29.95,
    description:
      "Organic spinach and fontina with shallot sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Italian"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be6",
    title: "Peppercorn and Garlic Rubbed Filet Mignon Tray",
    price: 29.95,
    description:
      "Served room temperature with horseradish cream. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be7",
    title: "Stuffed Filet Mignon with Blue Cheese Tray",
    price: 29.95,
    description:
      "Arugula and chive Madeira sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "French"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be8",
    title: "Stuffed Sirloin Tray",
    price: 29.95,
    description:
      "Spinach, roasted peppers and fresh mozzarella with mushroom Madeira. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be9",
    title: "Shepherd's Pie Tray",
    price: 16.5,
    description:
      "Ground sirloin layered with mushrooms, corn and topped with garlic whipped potatoes. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["British", "Irish", "Comfort Food"],
    mealType: ["Dinner"],
  },
  {
    id: "be10",
    title: "Traditional Beef Bourguignon Tray",
    price: 16.5,
    description:
      "Pearl onions, carrots and potatoes. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["French", "Comfort Food"],
    mealType: ["Dinner"],
  },
  {
    id: "be11",
    title: "Grilled Asian Sesame Marinated Skirt Steak Tray",
    price: 18.5,
    description:
      "Served on a bed of sauteed baby spinach. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Asian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "be12",
    title: "Filet Mignon Tray",
    price: 18.95,
    description:
      "Topped with sauteed mushrooms, caramelized onion and a red raspberry reduction. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["American", "French"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be13",
    title: "Grilled Chimichurri Skirt Steak Tray",
    price: 16.5,
    description:
      "Served on a bed of sauteed peppers and onions. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Argentinian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "be14",
    title: "Beef Tenderloin Tray",
    price: 18.95,
    description:
      "Topped with artichoke hearts, wild mushrooms and Bearnaise sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["American", "French"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be15",
    title: "Meatballs Tray",
    price: 12.95,
    description: "Choose your favorite sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner", "Appetizer"],
  },
  {
    id: "be16",
    title: "Meatloaf Tray",
    price: 14.95,
    description:
      "Plain or stuffed, with rich mushroom gravy. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["American", "Comfort Food"],
    mealType: ["Dinner"],
  },
  {
    id: "be17",
    title: "Sesame Beef and Asparagus Stir-Fry Tray",
    price: 14.95,
    description: "Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Asian"],
    mealType: ["Dinner"],
  },
  {
    id: "be18",
    title: "Stroganoff Tray",
    price: 14.95,
    description: "Served on a bed of egg noodles. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Russian", "American", "Comfort Food"],
    mealType: ["Dinner"],
  },
  {
    id: "be19",
    title: "Brisket of Beef Tray",
    price: 14.95,
    description:
      "Served with pineapple barbecue sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["American", "BBQ"],
    mealType: ["Dinner"],
  },
  {
    id: "be20",
    title: "Short Ribs Tray",
    price: 17.95,
    description:
      "Osso Buco braised in an aromatic red wine stock until fork tender and absolutely delicious. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Italian", "French", "Comfort Food"],
    mealType: ["Dinner"],
  },
  {
    id: "be21",
    title: "Braised Beef Short Ribs Tray",
    price: 16.5,
    description:
      "Served with baby carrots, turnips and parsnips. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["American", "European", "Comfort Food"],
    mealType: ["Dinner"],
  },
  {
    id: "be22",
    title: "Pacific Rim Beef Tray",
    price: 16.5,
    description:
      "Saute with ginger, onions, peppers and black bean sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Asian"],
    mealType: ["Dinner"],
  },
  {
    id: "be23",
    title: "Veal Toscana Tender Tray",
    price: 16.5,
    description:
      "Medallions of Plume de Veau veal with shiitake mushrooms, sun-dried tomatoes and a shallot cream sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be24",
    title: "Veal Marsala Tender Tray",
    price: 16.5,
    description:
      "Medallions of Plume de Veau veal with mushroom Marsala sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be25",
    title: "Veal Saltimbocca Tray",
    price: 16.5,
    description:
      "Medallions of veal topped with spinach, prosciutto and fontina in a sage white wine butter sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "be26",
    title: "Veal Daniella Tray",
    price: 16.5,
    description:
      "Tender medallions of Plume de Veau veal topped with jumbo lumb crabmeat, asparagus and a lobster sherry sauce on a bed of sauteed mushrooms. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Beef Entrees",
    minimum: 6,
    cuisine: ["American", "Seafood"],
    mealType: ["Dinner", "Fine Dining"],
  },

  // Pork Entrees
  {
    id: "pk1",
    title: "St. Louis Style Spare Ribs Tray",
    price: 18.95,
    description: "Black Jack BBQ sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Pork Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "BBQ"],
    mealType: ["Dinner"],
  },
  {
    id: "pk2",
    title: "Stuffed Pork Loin Tray",
    price: 18.95,
    description:
      "Apples and raisins in a bourbon brown sugar glaze. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Pork Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American"],
    mealType: ["Dinner"],
  },
  {
    id: "pk3",
    title: "12 Hour Braised Barbecue Pulled Pork Tray",
    price: 19.95,
    description: "Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Pork Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "BBQ"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "pk4",
    title: "Brandy and Brown Sugar Smoked Spiral Ham Tray",
    price: 19.95,
    description:
      "Served with Dijon and pommerey mustards. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Pork Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European"],
    mealType: ["Dinner", "Holiday"],
  },
  {
    id: "pk5",
    title: "Slow Braised Baby Back Ribs Tray",
    price: 19.95,
    description: "Homemade Black Jack BBQ sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Pork Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "BBQ"],
    mealType: ["Dinner"],
  },
  {
    id: "pk6",
    title: "Sweet and Sour Pork Tray",
    price: 19.95,
    description: "Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Pork Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Chinese", "Asian"],
    mealType: ["Dinner"],
  },
  {
    id: "pk7",
    title: "Pork Chops Tray",
    price: 19.95,
    description:
      "Served with hoisin ginger sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Pork Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Asian", "American"],
    mealType: ["Dinner"],
  },

  // Seafood Entrees - Adding ALL seafood dishes
  {
    id: "sf1",
    title: "Roasted Canadian Salmon Fillet Tray",
    price: 19.95,
    description:
      "Smoked paprika, lemon and herbs. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf2",
    title: "Dijon and Parmesan Crusted Salmon Fillet Tray",
    price: 19.95,
    description: "Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf3",
    title: "Balsamic and Orange Glazed Salmon Fillet Tray",
    price: 19.95,
    description: "Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf4",
    title: "Roasted Canadian Salmon Fillet with Lemon and Herbs Tray",
    price: 19.95,
    description:
      "Tomato, artichoke and basil relish. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Mediterranean", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf5",
    title: "Pan-Seared Salmon Tray",
    price: 19.95,
    description:
      "Served with caramelized and braised shallots on a bed of fennel and spinach. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "European", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf6",
    title: "Salmon with Teriyaki Glaze Tray",
    price: 19.95,
    description: "Black and white sesame seeds. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Asian", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf7",
    title: "Salmon with Miso Tray",
    price: 19.95,
    description:
      "Mirin and soy glaze and roasted sesame seeds. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Asian", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf8",
    title: "Baked Salmon Tray",
    price: 19.95,
    description:
      "Served with macadamia and Parmesan crust with an orange butter sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Hawaiian", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf9",
    title: "Salmon Infused with Green Tea Tray",
    price: 19.95,
    description:
      "Served with sake braised shiitakes. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["Asian", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf10",
    title: "Blackened Salmon Tray",
    price: 19.95,
    description:
      "Made in a tangy Creole tomato and champagne sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Creole", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf11",
    title: "Coconut Crusted Shrimp Tray",
    price: 21.95,
    description: "Served with pina colada sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Caribbean", "Seafood"],
    mealType: ["Dinner", "Appetizer"],
  },
  {
    id: "sf12",
    title: "Baked Gulf Shrimp Tray",
    price: 21.95,
    description: "Stuffed with lump crabmeat. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["American", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf13",
    title: "Grilled Shrimp Tray",
    price: 21.95,
    description: "Served with lemon and garlic. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Mediterranean", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf14",
    title: "Shrimp Scampi Tray",
    price: 21.95,
    description:
      "Served with a garlic and dry sherry wine sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Italian", "American", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf15",
    title: "Crisp Red Snapper Tray",
    price: 21.95,
    description:
      "Served with roasted tomato confit on a bed of spinach. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Mediterranean", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf16",
    title: "Perch Tray",
    price: 21.95,
    description: "Grilled with lime and tequila. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Mexican", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf17",
    title: "Braised Bass Tray",
    price: 21.95,
    description:
      "Served with artichokes and zucchini. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Mediterranean", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf18",
    title: "Halibut Tray",
    price: 45.95,
    description:
      "Roasted halibut, fresh fennel and figs on a bed of spaghetti squash. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["American", "European", "Seafood"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "sf19",
    title: "Striped Bass Tray",
    price: 34.95,
    description:
      "Topped with mango and avocado salsa. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Latin American", "Seafood"],
    mealType: ["Dinner", "Fine Dining"],
  },
  {
    id: "sf20",
    title: "Crispy Calamari Tray",
    price: 18.95,
    description:
      "Served with a Greek garlic sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Mediterranean", "Greek", "Seafood"],
    mealType: ["Appetizer", "Dinner"],
  },
  {
    id: "sf21",
    title: "Tuna Tray",
    price: 21.95,
    description:
      "Sesame crusted seared tuna steak served over bok choy. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Asian", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf22",
    title: "Flounder Tray",
    price: 21.95,
    description:
      "Crabmeat stuffed flounder with lemon wine sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["American", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "sf23",
    title: "Classic Paella Valencia Tray",
    price: 24.95,
    description:
      "Lobster, shrimp, clams, mussels, chicken and chorizo with saffron rice. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Seafood Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Spanish", "Seafood"],
    mealType: ["Dinner"],
  },

  // Vegetarian Entrees - Adding ALL vegetarian dishes
  {
    id: "ve1",
    title: "Roasted Vegetable Lasagna Tray",
    price: 18.95,
    description:
      "Layers of vegetables and cheese in a delightful red sauce. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve2",
    title: "Stuffed Portobello Tray",
    price: 18.95,
    description:
      "Comes with spinach, roasted peppers and smoked mozzarella. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve3",
    title: "Wild Mushroom and Broccoli Strudel Tray",
    price: 16.95,
    description: "Herbed creme fraiche. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["European", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve4",
    title: "Stuffed Peppers Tray",
    price: 15.95,
    description:
      "Comes with basmati ricem vegetables and roasted tomato glaze. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Mediterranean", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve5",
    title: "Curried Vegetable Stew Tray",
    price: 15.95,
    description:
      "Spicy curry garlic stew of carrots, potatoes, zucchini, garbanzo beans and tomatoes. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 10,
    serves: 1,
    cuisine: ["Indian", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve6",
    title: "Eggplant Rollatini Tray",
    price: 12.95,
    description:
      "Stuffed with ricotta cheese topped with marinara and fresh Parmesan. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve7",
    title: "Cheese-Less Vegetables Lasagna Tray",
    price: 12.95,
    description: "Served with tofu toppings. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["Italian", "Vegan"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve8",
    title: "Lasagna a la Verdura Tray",
    price: 12.95,
    description:
      "Served with fresh Swiss chard, yellow squash, carrots, red bell peppers, low fat cottage cheese and other cheeses. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve9",
    title: "Asian Tofu and Eggplant Tray",
    price: 12.95,
    description: "Sesame broccoli. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["Asian", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve10",
    title: "Roasted Tomato Tray",
    price: 12.95,
    description:
      "Goat cheese and caramelized onion tarts. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["American", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve11",
    title: "Vegan Quinoa Tray",
    price: 12.95,
    description:
      "Grilled zucchini, roasted peppers and spinach garlic tahini dip. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["Mediterranean", "Vegan"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve12",
    title: "Eggplant Napoleon Tray",
    price: 12.95,
    description:
      "Grilled eggplant layered with fresh mozzarella, basil and roasted tomatoes. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve13",
    title: "Stuffed Eggplant Tray",
    price: 12.95,
    description:
      "Served with wheat berry pilaf, spinach and corn. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["Mediterranean", "Vegetarian"],
    mealType: ["Dinner", "Lunch"],
  },
  {
    id: "ve14",
    title: "Hoisin Tofu and Eggplant Tray",
    price: 12.95,
    description:
      "Served with sauteed baby bok choy and Cambodian bean sprout. Served with a basket of brick oven bread and a side of garden salad.",
    category: "Entrees",
    subcategory: "Vegetarian Entrees",
    minimum: 6,
    cuisine: ["Asian", "Vegan"],
    mealType: ["Dinner", "Lunch"],
  },

  // Italian Pasta Dishes - Adding ALL pasta dishes
  {
    id: "ip1",
    title: "Pasta with Vodka Tomato Sauce Tray",
    price: 9.95,
    description: "Spinach, onions, fresh fennel and classic Italian zesty tomato sauce. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip2",
    title: "Orecchiete Tray",
    price: 9.95,
    description:
      "Portobello mushrooms, artichoke hearts, peas and roasted peppers with garlic cream. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip3",
    title: "Pasta Carbonara Tray",
    price: 9.95,
    description: "Cream based sauce with onions, bacon, peas, mushrooms and roasted veggies. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian", "American"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip4",
    title: "Pasta Pesto Tray",
    price: 9.95,
    description:
      "Served with pine nuts, diced fresh mozzarella and shredded Reggiano Parmesan cheese. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip5",
    title: "Pasta Primavera Tray",
    price: 9.95,
    description:
      "Fresh grilled garden vegetable medley sauteed in virgin olive oil, fresh garlic and spices. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip6",
    title: "Pasta Italiano Tray",
    price: 9.95,
    description:
      "Served with Italian Gorgonzola, mascarpone, Parmesan, eggplant and broccoli. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip7",
    title: "Pasta ala Vodka Tray",
    price: 9.95,
    description: "Served with baby peas and roasted plum tomatoes. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian", "American"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip8",
    title: "Pasta Aglio e Olio Tray",
    price: 9.95,
    description: "Served with virgin olive oil, garlic, fresh cut basil and tomato concasse. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip9",
    title: "Pasta Arrabiata Tray",
    price: 9.95,
    description:
      "A tangy dish with capers, Kalamata olives, tomatoes, garlic, onions and olive oil. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip10",
    title: "Cheese Ravioli Tray",
    price: 9.95,
    description: "Served with goat cheese, fresh tomato and basil sauce. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip11",
    title: "Gnocchi Tray",
    price: 9.95,
    description:
      "Served with zucchini potato pasta served with sauteed zucchini in a garlic and oil sauce. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "ip12",
    title: "Tortellini Tray",
    price: 9.95,
    description:
      "Served with sauteed shallots, sun-dried tomatoes, peppers and cremini mushrooms. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Pasta Dishes",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },

  // Italian Baked Pasta - Adding ALL baked pasta dishes
  {
    id: "bpasta1",
    title: "Baked Lasagna Primavera Tray",
    price: 10.95,
    description:
      "Made with roasted vegetables, ricotta and mozzarella cheeses, layered in pasta with basil marinara sauce. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "bpasta2",
    title: "Baked Orecchiette Tray",
    price: 10.95,
    description: "Served with spinach and mushrooms in 4 cheese sauce. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "bpasta3",
    title: "Baked Shells Tray",
    price: 10.95,
    description:
      "Served with steamed garlic broccoli and roasted peppers in a cheddar cream sauce. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["Italian", "American"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "bpasta4",
    title: "Baked Classic Mac and Cheese Tray",
    price: 10.95,
    description: "Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["American", "Comfort Food"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "bpasta5",
    title: "Baked Ziti Tray",
    price: 10.95,
    description:
      "Roasted eggplant, zucchini and herb roasted mushrooms in light cream sauce and Parmesan. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "bpasta6",
    title: "Baked Manicotti Tray",
    price: 10.95,
    description: "Served with basil marinara sauce and fresh mozzarella. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "bpasta7",
    title: "Classic Baked Ziti Tray",
    price: 10.95,
    description:
      "Served with ricotta and mozzarella topped with fresh grated Reggiano Parmesan cheese. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["Italian", "American"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "bpasta8",
    title: "Lasagna Alforno Tray",
    price: 10.95,
    description: "Layered pasta with fresh spinach, ricotta and Romano cheese. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },
  {
    id: "bpasta9",
    title: "Lasagna Rolls Tray",
    price: 10.95,
    description:
      "Fresh spinach, fresh ricotta, mozzarella and Parmesan Reggiano in a tomato basil sauce. Served with bread basket.",
    category: "Pasta",
    subcategory: "Italian Baked Pasta",
    minimum: 6,
    cuisine: ["Italian"],
    mealType: ["Lunch", "Dinner"],
  },

  // Italian Pasta Entrees - Adding ALL pasta entrees
  {
    id: "ipe1",
    title: "Baked Lasagna Bolognese Tray",
    price: 19.95,
    description:
      "Sauteed lean ground beef, spices and imported cheese in chunky basil with marinara sauce. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe2",
    title: "Ziti Tray",
    price: 19.95,
    description: "Served with country sausage, broccoli and peppers. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe3",
    title: "Ziti Pesto Tray",
    price: 19.95,
    description:
      "Rubbed and grilled chicken with roasted Roma tomato, broccoli and Parmesan cheese. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe4",
    title: "Spicy Shredded Beef Pasta Tray",
    price: 19.95,
    description: "Served with snow peas, peppers and soba noodles. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Asian", "Mexican"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe5",
    title: "Beef Stroganoff Tray",
    price: 19.95,
    description:
      "An old world favorite featuring beef smothered in sour cream mushroom sauce served over noodle. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Russian", "American", "Comfort Food"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe6",
    title: "Scampi Jumbo Shrimp Tray",
    price: 21.95,
    description:
      "Sauteed in garlic, butter and white wine reduction, served over linguine. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe7",
    title: "Bolognese Lasagna Tray",
    price: 19.95,
    description:
      "Our savory Bolognese sauce rolled in wide flat noodles with 3 Italian cheeses. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe8",
    title: "Spaghetti and Meatballs Tray",
    price: 19.95,
    description:
      "Seasoned ground sirloin rolled into succulent meatballs, simmered in our own marinara sauce. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe9",
    title: "Fettuccine Grilled Chicken Tray",
    price: 19.95,
    description: "Fresh spinach and basil in pink sauce. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "American"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe10",
    title: "Seafood Linguine Tray",
    price: 21.95,
    description:
      "Seasonally fresh seafood tossed in our own marinara sauce. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe11",
    title: "Rigatoni Tray",
    price: 21.95,
    description: "Served with salmon and sun-dried tomatoes. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "Seafood"],
    mealType: ["Dinner"],
  },
  {
    id: "ipe12",
    title: "Whole Wheat Linguine Tray",
    price: 18.95,
    description:
      "Shrimp, asparagus, fresh tomato, arugula, garlic and olive oil in roasted tomato and herb sauce. Served with brick oven bread and Caesar salad.",
    category: "Pasta",
    subcategory: "Italian Pasta Entrees",
    minimum: 8,
    serves: 1,
    cuisine: ["Italian", "Healthy", "Seafood"],
    mealType: ["Dinner"],
  },

  // Potato Accompaniments - Adding ALL potato sides
  {
    id: "side-p1",
    title: "Carrot Mashed Potatoes Tray",
    price: 4.75,
    description: "Mashed potatoes with carrots.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "Healthy"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p2",
    title: "Roasted Yukon Gold Potatoes Tray",
    price: 4.75,
    description: "Comes with fresh herbs.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "European"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p3",
    title: "Roasted Fingerling Potatoes Tray",
    price: 4.75,
    description: "Roasted fingerling potatoes.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "European"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p4",
    title: "Artichoke, Leek and Potato Gratin Tray",
    price: 4.75,
    description: "Potato gratin with artichoke and leek.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["French", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p5",
    title: "Roasted Red Potatoes Tray",
    price: 4.75,
    description: "Comes with sage and rosemary.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "Italian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p6",
    title: "Baked Scalloped Potatoes Tray",
    price: 4.75,
    description: "Comes with Bechamel sauce.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "European"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p7",
    title: "Sweet Potato Chunks Tray",
    price: 4.75,
    description: "Comes with honey orange zest and tarragon.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "Healthy"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p8",
    title: "Cajun Potato Wedges Tray",
    price: 4.75,
    description: "Oven roasted to perfection with roasted garlic and fresh herbs.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "Cajun"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p9",
    title: "Honey Orange Glazed Sweet Potatoes Tray",
    price: 4.75,
    description: "Comes with dried fruit and toasted pecans.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "Healthy"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p10",
    title: "Lemon Thyme Roasted Potatoes Tray",
    price: 4.75,
    description: "Roasted potatoes with lemon and thyme.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["Mediterranean", "European"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p11",
    title: "Yukon Gold Potato Tart Tray",
    price: 4.75,
    description: "Comes with truffles.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["French", "European"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p12",
    title: "Polenta with Parmesan Cheese Tray",
    price: 4.75,
    description: "Creamy polenta with Parmesan.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p13",
    title: "Wasabi Mashed Potatoes Tray",
    price: 4.75,
    description: "Mashed potatoes with wasabi.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["Asian", "American"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p14",
    title: "Classic Mashed Potato Tray",
    price: 4.75,
    description: "Traditional mashed potatoes.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "European", "Comfort Food"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p15",
    title: "Potatoes Gaspar Tray",
    price: 4.75,
    description: "Sauteed with scallions and garlic.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "Italian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-p16",
    title: "Mashed Sweet Potatoes Tray",
    price: 4.75,
    description: "Creamy mashed sweet potatoes.",
    category: "Sides",
    subcategory: "Potato Accompaniments",
    cuisine: ["American", "Healthy"],
    mealType: ["Side Dish"],
  },

  // Rice Accompaniments - Adding ALL rice sides
  {
    id: "side-r1",
    title: "Wild Mushroom Risotto Tray",
    price: 4.75,
    description: "Creamy risotto with wild mushrooms.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Italian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r2",
    title: "Jasmine Rice with Truffles and Scallions Tray",
    price: 4.75,
    description: "Fragrant jasmine rice with truffles.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Asian", "European"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r3",
    title: "Wild Rice Pilaf with Roasted Cubed Vegetables Tray",
    price: 4.75,
    description: "Wild rice with roasted vegetables.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["American", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r4",
    title: "Healthy Steamed White Rice Tray",
    price: 4.75,
    description: "Simple steamed white rice.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Asian", "Healthy"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r5",
    title: "Healthy Steamed Brown Rice Tray",
    price: 4.75,
    description: "Nutritious steamed brown rice.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Healthy", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r6",
    title: "Uzbek Carrots with Raisin Rice Pilaf Tray",
    price: 4.75,
    description: "Rice pilaf with carrots and raisins.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Central Asian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r7",
    title: "Mexican Style Rice Pilaf Tray",
    price: 4.75,
    description: "Yellow rice, peppers, onions and tomatoes.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Mexican"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r8",
    title: "Koshari Special Mediterranean Rice Dish Tray",
    price: 4.75,
    description: "Served with lentil, chickpeas and fried shallots.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Egyptian", "Mediterranean", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r9",
    title: "Yellow Fried Rice with Vegetables Tray",
    price: 4.75,
    description: "Fried rice with mixed vegetables.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Asian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r10",
    title: "Basmati Rice with Shiitake Mushrooms Tray",
    price: 4.75,
    description: "Fragrant basmati with mushrooms.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Asian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r11",
    title: "Spinach and Mushrooms Rice Pilaf Tray",
    price: 4.75,
    description: "Rice pilaf with spinach and mushrooms.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["American", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r12",
    title: "Spanish Rice Tray",
    price: 4.75,
    description: "Arroz con gandules.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Latin American", "Puerto Rican"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-r13",
    title: "Creole Rice Tray",
    price: 4.75,
    description: "Carrots, corn, red pepper and tomatoes.",
    category: "Sides",
    subcategory: "Rice Accompaniments",
    cuisine: ["Creole", "American"],
    mealType: ["Side Dish"],
  },

  // Vegetable Accompaniments - Adding ALL vegetable sides
  {
    id: "side-v1",
    title: "Roasted Butternut Squash",
    price: 5.5,
    description: "Served with dried fruits.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["American", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v2",
    title: "Sauteed Spinach",
    price: 5.5,
    description: "Served with toasted pine nuts.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Mediterranean", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v3",
    title: "Steamed Asparagus",
    price: 5.5,
    description: "Served with citrus vinaigrette.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Healthy", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v4",
    title: "Steamed Garden Vegetables Tray",
    price: 4.75,
    description: "Served with fresh herbs.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["American", "Healthy", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v5",
    title: "Grilled Assorted Vegetables Tray",
    price: 4.75,
    description: "Seasonal grilled vegetables.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Mediterranean", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v6",
    title: "Grilled Asparagus and Roasted Bell Pepper Tray",
    price: 4.75,
    description: "Portobello mushrooms and grilled onions.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Mediterranean", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v7",
    title: "Roasted Vegetable Ratouille Tray",
    price: 4.75,
    description: "Classic French vegetable stew.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["French", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v8",
    title: "Roasted Orange Glazed Petite Carrots Tray",
    price: 4.75,
    description: "Sweet glazed baby carrots.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["American", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v9",
    title: "Sauteed Snap Peas and Mushrooms Tray",
    price: 4.75,
    description: "Crisp snap peas with mushrooms.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Asian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v10",
    title: "Sauteed Green Beans with Fresh Garlic Tray",
    price: 4.75,
    description: "Fresh green beans with garlic.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["American", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v11",
    title: "Sauteed Carrots and Peas Tray",
    price: 4.75,
    description: "Classic carrot and pea combination.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["American", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v12",
    title: "Sauteed String Beans Almandine Tray",
    price: 4.75,
    description: "Served with teriyaki sauce, almonds and roasted peppers.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["American", "Asian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v13",
    title: "Sauteed String Beans with Shallots and Shiitake Mushrooms Tray",
    price: 4.75,
    description: "Green beans with shallots and mushrooms.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Asian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v14",
    title: "Sauteed Haricot Vert Tray",
    price: 4.75,
    description: "Shaved fennel, zucchini and tarragon.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["French", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v15",
    title: "Sauteed Shiitake Mushrooms Tray",
    price: 4.75,
    description: "Served with scallions and sesame seeds.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Asian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v16",
    title: "Sauteed Baby Bok Choy Tray",
    price: 4.75,
    description: "Served with teriyaki glaze and sesame seeds.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Asian", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v17",
    title: "Sauteed Broccoli Tray",
    price: 4.75,
    description: "Served with fresh garlic and extra virgin olive oil.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Mediterranean", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v18",
    title: "Fresh Tomato and Eggplant Gratin Tray",
    price: 4.75,
    description: "Baked tomato and eggplant.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["Mediterranean", "Vegetarian"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v19",
    title: "Creamed Spinach Tray",
    price: 4.75,
    description: "Served with a dash of Parmesan Romano cheese.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["American", "European"],
    mealType: ["Side Dish"],
  },
  {
    id: "side-v20",
    title: "Carrots Vichy Tray",
    price: 4.75,
    description: "Slow cooked with onions, thyme, Chardonnay wine and butter.",
    category: "Sides",
    subcategory: "Vegetable Accompaniments",
    cuisine: ["French", "Vegetarian"],
    mealType: ["Side Dish"],
  },

  // Desserts - Adding ALL desserts
  {
    id: "dessert1",
    title: "Chocolate Heaven Tray",
    price: 9.95,
    description:
      "Chocolate fudge brownies, chocolate ganache cups, chocolate cheesecake bars, chocolate eclairs, chocolate cream puffs, Belgian chocolate bittersweet and white chocolate dipped strawberries.",
    category: "Desserts",
    subcategory: "Dessert Platters",
    minimum: 6,
    cuisine: ["American", "Belgian", "Dessert"],
    mealType: ["Dessert"],
  },
  {
    id: "dessert2",
    title: "Mini Cheesecakes Tray",
    price: 8.95,
    description:
      "An assortment of mini cheesecakes, including plain, chocolate swirl, strawberry, banana blueberry and pumpkin.",
    category: "Desserts",
    subcategory: "Dessert Platters",
    minimum: 6,
    serves: 1,
    cuisine: ["American", "Dessert"],
    mealType: ["Dessert"],
  },
  {
    id: "dessert3",
    title: "Petite Fours Tray",
    price: 8.95,
    description: "Bite sized layer cakes filled with assorted creams and presented on a silver platter.",
    category: "Desserts",
    subcategory: "Dessert Platters",
    minimum: 6,
    serves: 1,
    cuisine: ["French", "Dessert"],
    mealType: ["Dessert"],
  },
  {
    id: "dessert4",
    title: "Exotic Sliced Fruits and Berries Platter",
    price: 8.95,
    description: "Presentations of sliced fruit with decorative garnish",
    category: "Desserts",
    subcategory: "Dessert Platters",
    minimum: 6,
    serves: 1,
    cuisine: ["Healthy", "Fruit", "Dessert"],
    mealType: ["Dessert", "Snack"],
  },
  {
    id: "dessert5",
    title: "Ice Cream Sundae Bar",
    price: 19.95,
    description: "Assorted freshly made ice cream with your choice of five different toppings.",
    category: "Desserts",
    subcategory: "Dessert Platters",
    minimum: 15,
    serves: 1,
    cuisine: ["American", "Dessert"],
    mealType: ["Dessert"],
  },
  {
    id: "dessert6",
    title: "Pie",
    price: 26.0,
    description: "Standard pies are 9 inch round.",
    category: "Desserts",
    subcategory: "Dessert Platters",
    serves: 9,
    cuisine: ["American", "Dessert"],
    mealType: ["Dessert"],
  },
  {
    id: "dessert7",
    title: "Dessert and Fruit Tray",
    price: 14.95,
    description: "Dessert platter with sliced fruit.",
    category: "Desserts",
    subcategory: "Dessert Platters",
    serves: 1,
    cuisine: ["American", "Dessert"],
    mealType: ["Dessert"],
  },

  // Beverages
  {
    id: "bev1",
    title: "Snapple",
    price: 3.99,
    description: "Assorted Snapple flavors.",
    category: "Beverages",
    subcategory: "Cold Beverages",
    serves: 1,
    cuisine: ["American"],
    mealType: ["Beverage"],
  },
  {
    id: "bev2",
    title: "San Pellegrino",
    price: 3.95,
    description: "San Pellegrino sparkling water.",
    category: "Beverages",
    subcategory: "Cold Beverages",
    serves: 1,
    cuisine: ["Italian"],
    mealType: ["Beverage"],
  },
  {
    id: "bev3",
    title: "Perrier",
    price: 3.95,
    description: "Perrier sparkling water.",
    category: "Beverages",
    subcategory: "Cold Beverages",
    serves: 1,
    cuisine: ["French"],
    mealType: ["Beverage"],
  },
  {
    id: "bev4",
    title: "Individual Juice",
    price: 2.95,
    description: "Individual juice bottles.",
    category: "Beverages",
    subcategory: "Cold Beverages",
    cuisine: ["American"],
    mealType: ["Beverage"],
  },
]

export default function MenuPage() {
  const [searchTerm, setSearchTerm] = useState("")
  const [selectedCategory, setSelectedCategory] = useState<string>("")
  const [selectedSubcategory, setSelectedSubcategory] = useState<string>("")
  const [selectedCuisines, setSelectedCuisines] = useState<string[]>([])
  const [selectedMealTypes, setSelectedMealTypes] = useState<string[]>([])
  const [quantities, setQuantities] = useState<Record<string, number>>({})
  const [cart, setCart] = useState<Record<string, number>>({})
  const { toast } = useToast()

  const categories = Array.from(new Set(menuData.map((item) => item.category)))
  const subcategories = selectedCategory
    ? Array.from(new Set(menuData.filter((item) => item.category === selectedCategory).map((item) => item.subcategory)))
    : []

  const cuisines = Array.from(new Set(menuData.flatMap((item) => item.cuisine || []))).sort()

  const mealTypes = Array.from(new Set(menuData.flatMap((item) => item.mealType || []))).sort()

  const filteredItems = menuData.filter((item) => {
    const matchesSearch =
      !searchTerm ||
      item.title.toLowerCase().includes(searchTerm.toLowerCase()) ||
      item.description.toLowerCase().includes(searchTerm.toLowerCase())

    const matchesCategory = !selectedCategory || item.category === selectedCategory
    const matchesSubcategory = !selectedSubcategory || item.subcategory === selectedSubcategory
    const matchesCuisine = selectedCuisines.length === 0 || selectedCuisines.some((c) => item.cuisine?.includes(c))
    const matchesMealType = selectedMealTypes.length === 0 || selectedMealTypes.some((m) => item.mealType?.includes(m))

    return matchesSearch && matchesCategory && matchesSubcategory && matchesCuisine && matchesMealType
  })

  const groupedItems = categories.reduce(
    (acc, category) => {
      acc[category] = filteredItems.filter((item) => item.category === category)
      return acc
    },
    {} as Record<string, MenuItem[]>,
  )

  const updateQuantity = (id: string, delta: number) => {
    setQuantities((prev) => ({
      ...prev,
      [id]: Math.max(1, (prev[id] || 1) + delta),
    }))
  }

  const calculateTotal = (id: string) => {
    const item = menuData.find((i) => i.id === id)
    if (!item) return

    const qty = quantities[id] || 1
    const total = item.price * qty

    toast({
      title: "Calculation",
      description: `${qty} × $${item.price.toFixed(2)} = $${total.toFixed(2)}`,
    })
  }

  const addToCart = (id: string) => {
    const qty = quantities[id] || 1
    setCart((prev) => ({
      ...prev,
      [id]: (prev[id] || 0) + qty,
    }))

    const item = menuData.find((i) => i.id === id)
    toast({
      title: "Added to Cart",
      description: `${qty} × ${item?.title}`,
    })
  }

  const clearFilters = () => {
    setSearchTerm("")
    setSelectedCategory("")
    setSelectedSubcategory("")
    setSelectedCuisines([])
    setSelectedMealTypes([])
  }

  const toggleCuisine = (cuisine: string) => {
    setSelectedCuisines((prev) => (prev.includes(cuisine) ? prev.filter((c) => c !== cuisine) : [...prev, cuisine]))
  }

  const toggleMealType = (mealType: string) => {
    setSelectedMealTypes((prev) => (prev.includes(mealType) ? prev.filter((m) => m !== mealType) : [...prev, mealType]))
  }

  const totalCartItems = Object.values(cart).reduce((sum, qty) => sum + qty, 0)

  return (
    <div className="min-h-screen bg-white">
      <nav className="fixed top-0 w-full bg-white/98 backdrop-blur-md z-50 shadow-sm">
        <div className="max-w-[1400px] mx-auto px-8">
          <div className="flex items-center justify-between h-24">
            <div className="font-serif text-2xl font-bold text-[#d4af37] tracking-[2px]">MGC</div>

            <ul className="hidden md:flex gap-12 list-none">
              <li>
                <Link
                  href="/"
                  className="text-gray-900 font-medium text-[0.95rem] tracking-wider uppercase transition-colors hover:text-[#d4af37]"
                >
                  Home
                </Link>
              </li>
              <li>
                <Link
                  href="/menu"
                  className="text-[#d4af37] font-medium text-[0.95rem] tracking-wider uppercase transition-colors hover:text-[#d4af37]"
                >
                  Menu
                </Link>
              </li>
              <li>
                <Link
                  href="/order"
                  className="text-gray-900 font-medium text-[0.95rem] tracking-wider uppercase transition-colors hover:text-[#d4af37]"
                >
                  Order Now
                </Link>
              </li>
              <li>
                <Link
                  href="/about"
                  className="text-gray-900 font-medium text-[0.95rem] tracking-wider uppercase transition-colors hover:text-[#d4af37]"
                >
                  About Us
                </Link>
              </li>
              <li>
                <Link
                  href="/who-we-serve"
                  className="text-gray-900 font-medium text-[0.95rem] tracking-wider uppercase transition-colors hover:text-[#d4af37]"
                >
                  Who We Serve
                </Link>
              </li>
              <li>
                <Link
                  href="/testimonials"
                  className="text-gray-900 font-medium text-[0.95rem] tracking-wider uppercase transition-colors hover:text-[#d4af37]"
                >
                  Testimonials
                </Link>
              </li>
            </ul>

            <div className="md:hidden flex-1 mx-4 overflow-x-auto scrollbar-hide">
              <ul className="flex gap-3 list-none">
                <li>
                  <Link
                    href="/"
                    className="text-gray-900 font-medium text-xs tracking-wider uppercase whitespace-nowrap transition-colors hover:text-[#d4af37]"
                  >
                    Home
                  </Link>
                </li>
                <li>
                  <Link
                    href="/menu"
                    className="text-[#d4af37] font-medium text-xs tracking-wider uppercase whitespace-nowrap transition-colors hover:text-[#d4af37]"
                  >
                    Menu
                  </Link>
                </li>
                <li>
                  <Link
                    href="/order"
                    className="text-gray-900 font-medium text-xs tracking-wider uppercase whitespace-nowrap transition-colors hover:text-[#d4af37]"
                  >
                    Order
                  </Link>
                </li>
                <li>
                  <Link
                    href="/about"
                    className="text-gray-900 font-medium text-xs tracking-wider uppercase whitespace-nowrap transition-colors hover:text-[#d4af37]"
                  >
                    About
                  </Link>
                </li>
                <li>
                  <Link
                    href="/who-we-serve"
                    className="text-gray-900 font-medium text-xs tracking-wider uppercase whitespace-nowrap transition-colors hover:text-[#d4af37]"
                  >
                    Serve
                  </Link>
                </li>
                <li>
                  <Link
                    href="/testimonials"
                    className="text-gray-900 font-medium text-xs tracking-wider uppercase whitespace-nowrap transition-colors hover:text-[#d4af37]"
                  >
                    Reviews
                  </Link>
                </li>
              </ul>
            </div>

            <button className="relative">
              <ShoppingCart className="h-6 w-6 text-gray-600 hover:text-[#d4af37] transition-colors" />
              {totalCartItems > 0 && (
                <span className="absolute -top-2 -right-2 bg-[#d4af37] text-white text-xs rounded-full h-5 w-5 flex items-center justify-center">
                  {totalCartItems}
                </span>
              )}
            </button>
          </div>
        </div>
      </nav>

      <div className="pt-32 pb-8 px-8 text-center bg-gradient-to-b from-gray-50 to-white">
        <h1 className="font-serif text-5xl font-bold text-gray-900 mb-2">Our Menu</h1>
        <div className="w-20 h-0.5 bg-gradient-to-r from-transparent via-[#d4af37] to-transparent mx-auto my-4"></div>
        <p className="text-gray-600 tracking-wider text-sm">Exquisite cuisine crafted for your special occasions</p>
      </div>

      <div className="max-w-[1400px] mx-auto px-8 py-6 bg-gray-50">
        <div className="mb-4">
          <Input
            type="text"
            placeholder="Search for dishes..."
            value={searchTerm}
            onChange={(e) => setSearchTerm(e.target.value)}
            className="w-full px-4 py-3 text-[0.95rem] border-2 border-gray-200 rounded-none focus:border-[#d4af37] focus-visible:ring-0 focus-visible:ring-offset-0"
          />
        </div>

        <div className="space-y-4">
          <div className="bg-white p-4 border border-gray-200">
            <h3 className="font-serif text-lg font-semibold text-gray-900 mb-3 flex items-center gap-2">
              Cuisine Type
            </h3>
            <div className="flex flex-wrap gap-2">
              {cuisines.map((cuisine) => (
                <label
                  key={cuisine}
                  className={`flex items-center gap-2 cursor-pointer px-3 py-2 border transition-all ${
                    selectedCuisines.includes(cuisine)
                      ? "bg-[#d4af37] border-[#d4af37] text-white"
                      : "bg-white border-gray-200 hover:border-[#d4af37] hover:bg-gray-50"
                  }`}
                >
                  <input
                    type="checkbox"
                    checked={selectedCuisines.includes(cuisine)}
                    onChange={() => toggleCuisine(cuisine)}
                    className="w-4 h-4 cursor-pointer accent-[#d4af37]"
                  />
                  <span className="text-sm">{cuisine}</span>
                </label>
              ))}
            </div>
          </div>

          <div className="bg-white p-4 border border-gray-200">
            <h3 className="font-serif text-lg font-semibold text-gray-900 mb-3 flex items-center gap-2">Meal Type</h3>
            <div className="flex flex-wrap gap-2">
              {mealTypes.map((mealType) => (
                <label
                  key={mealType}
                  className={`flex items-center gap-2 cursor-pointer px-3 py-2 border transition-all ${
                    selectedMealTypes.includes(mealType)
                      ? "bg-[#d4af37] border-[#d4af37] text-white"
                      : "bg-white border-gray-200 hover:border-[#d4af37] hover:bg-gray-50"
                  }`}
                >
                  <input
                    type="checkbox"
                    checked={selectedMealTypes.includes(mealType)}
                    onChange={() => toggleMealType(mealType)}
                    className="w-4 h-4 cursor-pointer accent-[#d4af37]"
                  />
                  <span className="text-sm">{mealType}</span>
                </label>
              ))}
            </div>
          </div>

          <div className="bg-white p-4 border border-gray-200">
            <h3 className="font-serif text-base font-semibold text-gray-900 mb-3 flex items-center gap-2">
              Food Categories
            </h3>
            <div className="flex flex-wrap gap-2">
              {categories.map((category) => (
                <label
                  key={category}
                  className={`flex items-center gap-2 cursor-pointer px-3 py-2 border transition-all ${
                    selectedCategory === category
                      ? "bg-[#d4af37] border-[#d4af37] text-white"
                      : "bg-white border-gray-200 hover:border-[#d4af37] hover:bg-gray-50"
                  }`}
                >
                  <input
                    type="checkbox"
                    checked={selectedCategory === category}
                    onChange={() => {
                      setSelectedCategory(category === selectedCategory ? "" : category)
                      setSelectedSubcategory("")
                    }}
                    className="w-4 h-4 cursor-pointer accent-[#d4af37]"
                  />
                  <span className="text-sm">{category}</span>
                </label>
              ))}
            </div>
          </div>

          <button
            onClick={clearFilters}
            className="mt-2 w-full px-6 py-3 bg-gray-900 text-white font-medium text-sm tracking-wider transition-colors hover:bg-[#d4af37]"
          >
            Clear All Filters
          </button>
        </div>

        <div className="text-center py-3 text-base text-gray-600">
          Showing {filteredItems.length} of {menuData.length} items
        </div>
      </div>

      {/* Menu Items */}
      <div className="max-w-[1400px] mx-auto px-8 py-8">
        {selectedCategory ? (
          // Show filtered items in grid when category is selected
          <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-5 gap-6">
            {filteredItems.map((item) => (
              <div
                key={item.id}
                className="bg-white border border-gray-200 hover:border-[#d4af37] hover:shadow-lg transition-all duration-300 hover:-translate-y-1"
              >
                <div className="w-full h-[200px] bg-gradient-to-br from-gray-100 to-gray-200 flex items-center justify-center overflow-hidden">
                  <img
                    src={`/.jpg?height=200&width=300&query=${encodeURIComponent(item.title)}`}
                    alt={item.title}
                    className="w-full h-full object-cover"
                  />
                </div>

                <div className="p-4">
                  <div className="flex justify-between items-start mb-2">
                    <h3 className="font-serif text-xl font-semibold text-gray-900 leading-tight">{item.title}</h3>
                    <span className="text-xl font-semibold text-[#d4af37] whitespace-nowrap ml-2">
                      ${item.price.toFixed(2)}
                    </span>
                  </div>

                  <p className="text-sm text-gray-600 mb-3 leading-relaxed">{item.description}</p>

                  <div className="flex flex-wrap gap-2 mb-3">
                    <span className="text-xs px-2 py-1 bg-gray-100 text-gray-600 rounded-full">{item.subcategory}</span>
                    {item.minimum && (
                      <span className="text-xs px-2 py-1 bg-gray-100 text-gray-600 rounded-full">
                        Min: {item.minimum}
                      </span>
                    )}
                  </div>

                  <div className="flex items-center gap-3 mb-3">
                    <span className="text-xs text-gray-600">Quantity:</span>
                    <div className="flex items-center gap-2">
                      <button
                        onClick={() => updateQuantity(item.id, -1)}
                        className="w-7 h-7 border border-[#d4af37] bg-white text-[#d4af37] flex items-center justify-center text-lg transition-colors hover:bg-[#d4af37] hover:text-white"
                      >
                        -
                      </button>
                      <input
                        type="number"
                        value={quantities[item.id] || 1}
                        onChange={(e) =>
                          setQuantities((prev) => ({
                            ...prev,
                            [item.id]: Math.max(1, Number.parseInt(e.target.value) || 1),
                          }))
                        }
                        className="w-11 text-center border border-gray-200 py-1 text-[0.95rem]"
                        min="1"
                      />
                      <button
                        onClick={() => updateQuantity(item.id, 1)}
                        className="w-7 h-7 border border-[#d4af37] bg-white text-[#d4af37] flex items-center justify-center text-lg transition-colors hover:bg-[#d4af37] hover:text-white"
                      >
                        +
                      </button>
                    </div>
                  </div>

                  <div className="flex gap-2">
                    <Button
                      size="sm"
                      variant="outline"
                      className="flex-1 bg-transparent text-xs border-gray-200 hover:bg-gray-50"
                      onClick={() => calculateTotal(item.id)}
                    >
                      <Calculator className="h-3 w-3 mr-1" />
                      Calculate
                    </Button>
                    <Button
                      size="sm"
                      className="flex-1 bg-[#d4af37] hover:bg-[#b8941f] text-xs"
                      onClick={() => addToCart(item.id)}
                    >
                      <ShoppingCart className="h-3 w-3 mr-1" />
                      Add
                    </Button>
                  </div>
                </div>
              </div>
            ))}
          </div>
        ) : (
          <div className="space-y-12">
            {categories.map((category) => {
              const categoryItems = groupedItems[category]
              if (!categoryItems || categoryItems.length === 0) return null

              return (
                <section key={category} className="scroll-mt-24">
                  <h2 className="font-serif text-[2.5rem] font-bold text-gray-900 mb-6 text-center">{category}</h2>

                  <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-5 gap-6 mb-12">
                    {categoryItems.map((item) => (
                      <div
                        key={item.id}
                        className="bg-white border border-gray-200 hover:border-[#d4af37] hover:shadow-lg transition-all duration-300 hover:-translate-y-1"
                      >
                        <div className="w-full h-[200px] bg-gradient-to-br from-gray-100 to-gray-200 flex items-center justify-center overflow-hidden">
                          <img
                            src={`/.jpg?height=200&width=300&query=${encodeURIComponent(item.title)}`}
                            alt={item.title}
                            className="w-full h-full object-cover"
                          />
                        </div>

                        <div className="p-4">
                          <div className="flex justify-between items-start mb-2">
                            <h3 className="font-serif text-xl font-semibold text-gray-900 leading-tight">
                              {item.title}
                            </h3>
                            <span className="text-xl font-semibold text-[#d4af37] whitespace-nowrap ml-2">
                              ${item.price.toFixed(2)}
                            </span>
                          </div>

                          <p className="text-sm text-gray-600 mb-3 leading-relaxed">{item.description}</p>

                          <div className="flex flex-wrap gap-2 mb-3">
                            <span className="text-xs px-2 py-1 bg-gray-100 text-gray-600 rounded-full">
                              {item.subcategory}
                            </span>
                            {item.minimum && (
                              <span className="text-xs px-2 py-1 bg-gray-100 text-gray-600 rounded-full">
                                Min: {item.minimum}
                              </span>
                            )}
                          </div>

                          <div className="flex items-center gap-3 mb-3">
                            <span className="text-xs text-gray-600">Quantity:</span>
                            <div className="flex items-center gap-2">
                              <button
                                onClick={() => updateQuantity(item.id, -1)}
                                className="w-7 h-7 border border-[#d4af37] bg-white text-[#d4af37] flex items-center justify-center text-lg transition-colors hover:bg-[#d4af37] hover:text-white"
                              >
                                -
                              </button>
                              <input
                                type="number"
                                value={quantities[item.id] || 1}
                                onChange={(e) =>
                                  setQuantities((prev) => ({
                                    ...prev,
                                    [item.id]: Math.max(1, Number.parseInt(e.target.value) || 1),
                                  }))
                                }
                                className="w-11 text-center border border-gray-200 py-1 text-[0.95rem]"
                                min="1"
                              />
                              <button
                                onClick={() => updateQuantity(item.id, 1)}
                                className="w-7 h-7 border border-[#d4af37] bg-white text-[#d4af37] flex items-center justify-center text-lg transition-colors hover:bg-[#d4af37] hover:text-white"
                              >
                                +
                              </button>
                            </div>
                          </div>

                          <div className="flex gap-2">
                            <Button
                              size="sm"
                              variant="outline"
                              className="flex-1 bg-transparent text-xs border-gray-200 hover:bg-gray-50"
                              onClick={() => calculateTotal(item.id)}
                            >
                              <Calculator className="h-3 w-3 mr-1" />
                              Calculate
                            </Button>
                            <Button
                              size="sm"
                              className="flex-1 bg-[#d4af37] hover:bg-[#b8941f] text-xs"
                              onClick={() => addToCart(item.id)}
                            >
                              <ShoppingCart className="h-3 w-3 mr-1" />
                              Add
                            </Button>
                          </div>
                        </div>
                      </div>
                    ))}
                  </div>
                </section>
              )
            })}
          </div>
        )}

        {filteredItems.length === 0 && (
          <div className="text-center py-12">
            <p className="text-gray-600 text-lg">No items found matching your criteria.</p>
            <button
              onClick={clearFilters}
              className="mt-4 px-6 py-3 bg-[#d4af37] text-white hover:bg-[#b8941f] transition-colors"
            >
              Clear Filters
            </button>
          </div>
        )}
      </div>
    </div>
  )
}
