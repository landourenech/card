// --- app/xxx/page.tsx ---
// Ce fichier est la page principale qui importe les données et le composant AllProduct pour afficher la liste des produits.

import AllProduct from "@/components/card/allProduct"; // Import du composant AllProduct
import data from "./data.json"; // Import des données JSON des produits

export default function Page() {
  return (
    <main>
      {/* Affichage du composant AllProduct en lui passant les données en props */}
      <AllProduct data={data} />
    </main>
  );
}









// --- data.json ---
// Ce fichier contient un tableau JSON représentant une liste de produits avec leurs propriétés.

[
    {
      "id": 1,
      "name": "name",
      "description": "lorem",
      "image": "/gabon.png",
      "price": 1000
    },
    {
        "id": 2,
        "name": "name",
        "description": "lorem",
        "image": "/gabon.png",
        "price": 1000
      }
      ,
    {
        "id": 3,
        "name": "name",
        "description": "lorem",
        "image": "/gabon.png",
        "price": 1000
      },
      {
          "id": 4,
          "name": "name",
          "description": "lorem",
          "image": "/gabon.png",
          "price": 1000
        },
        {
            "id": 5,
            "name": "name",
            "description": "lorem",
            "image": "/gabon.png",
            "price": 1000
          }
          ,
        {
            "id": 6,
            "name": "name",
            "description": "lorem",
            "image": "/gabon.png",
            "price": 1000
          },
          {
              "id": 7,
              "name": "name",
              "description": "lorem",
              "image": "/gabon.png",
              "price": 1000
            }
      
  ]









  

// --- components/allProduct.tsx ---
// Ce composant reçoit un tableau de produits et affiche chaque produit en utilisant le composant Product.

import Product from "./product";

interface ProductItem {
  id: number;
  image: string;
  name: string;
  description: string;
  price: number;
}

interface ProduitAll {
  data: ProductItem[]; // Props attendues : un tableau de produits
}

export default function AllProduct({ data }: ProduitAll) {
  return (
    // Affichage en grille de 5 colonnes
    <main className="grid grid-cols-5 md:*grid-cols">
      {/* Pour chaque produit, on affiche un composant Product avec ses props */}
      {data.map((item) => (
        <Product
          key={item.id}
          id={item.id}
          name={item.name}
          description={item.description}
          price={item.price}
          image={item.image}
        />
      ))}
    </main>
  );
}












// --- components/product.tsx ---
// Ce composant affiche les détails d’un produit individuel : image, nom, description, prix.

import Image from "next/image";

interface ProductItem {
  id: number;
  image: string;
  name: string;
  description: string;
  price: number;
}

export default function Product({ image, description, name, price }: ProductItem) {
  return (
    <main className="flex">
      {/* Image du produit avec Next.js Image optimisé */}
      <Image src={image} width={50} height={100} alt={name} />
      <h1>{name}</h1>
      <p>{description}</p>
      <p className="text-red-500">{price} XAF</p>
    </main>
  );
}
