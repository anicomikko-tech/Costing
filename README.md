# Costing
Cost for Food
import { createSlice, PayloadAction } from '@reduxjs/toolkit';
import { Sale } from '@types/index';

interface SaleState {
  items: Sale[];
  loading: boolean;
  error: string | null;
}

const initialState: SaleState = {
  items: [],
  loading: false,
  error: null,
};

const saleSlice = createSlice({
  name: 'sales',
  initialState,
  reducers: {
    setSales: (state, action: PayloadAction<Sale[]>) => {
      state.items = action.payload;
      state.loading = false;
    },
    addSale: (state, action: PayloadAction<Sale>) => {
      state.items.unshift(action.payload);
    },
    removeSale: (state, action: PayloadAction<string>) => {
      state.items = state.items.filter(s => s.id !== action.payload);
    },
    setLoading: (state, action: PayloadAction<boolean>) => {
      state.loading = action.payload;
    },
    setError: (state, action: PayloadAction<string | null>) => {
      state.error = action.payload;
    },
  },
});

export const { setSales, addSale, removeSale, setLoading, setError } = saleSlice.actions;

export default saleSlice.reducer;
